Architectural Decision Record
Title

API Versioning Strategy: Use URL Path or URI Parameter
Context

Our application provides a RESTful API to clients. As the application evolves, we need a strategy to handle changes to the API without disrupting existing clients. Versioning the API is essential to manage these changes. The main strategies considered are versioning through the URL path (e.g., /api/v1/resource) or through a URI parameter (e.g., /api/resource?v=1).
Decision

We will implement API versioning using the URL path.
Status

Accepted
Consequences

    Positive:
        Clear Separation: Each version of the API is distinctly separated by the URL path, making it easy to understand which version is being used.
        Cache-Friendly: URLs with versioning in the path are more cacheable by intermediaries like CDNs and proxies.
        Best Practice Alignment: This approach aligns with common RESTful API versioning practices, making it familiar to developers.
    Negative:
        URL Length: URLs may become longer and slightly more complex.
        Routing Complexity: May add complexity to the routing configuration in the application.

Alternatives Considered

    URI Parameter Versioning:
        Pros: Keeps the base URL clean and short.
        Cons: Less cache-friendly and can lead to confusion if query parameters are used extensively for other purposes.

    Header Versioning:
        Pros: Keeps URLs clean and allows versioning at the protocol level.
        Cons: Less visible and discoverable for developers, can complicate API client configuration.

Rationale

We chose URL path versioning because it provides a clear and intuitive way for clients to specify the API version they want to use. This method is widely adopted in the industry and offers better support for caching mechanisms. Although it slightly increases URL length, the benefits of clarity and cache-friendliness outweigh this drawback. URI parameter versioning was not chosen due to its potential to create less cache-friendly URLs and possible confusion with other query parameters.
Related Decisions

    ADR-002: API Authentication Method
    ADR-004: Use of OpenAPI for API Documentation

Date

2024-05-23
Author

John Smith, Lead Architect
