# Backend for OmniGpt application

[](https://github.com/superstack-digital/padel-backend#backend-for-padel-application)

This repository contains a backend application for managing jira, notion, integration employing a simplified Domain-Driven Design (DDD) approach. The application is designed to be deployed on Supabase Edge Functions, providing a scalable, serverless backend.

## Simplified Project Structure

The application is organized into a few key directories:

```
src/
|-- domain/
|   |-- embeddings/
|       |-- Embedding.ts            // Embedding entity with properties and methods
|       |-- EmbeddingInterface.ts   // Interface for Embedding data access
|       |-- EmbeddingRepository.ts  // Supabase implementation of EmbeddingInterface
|	|-- data_sources/
|   	|-- Jira.ts                // Jira data source using LlamaIndex
|   	|-- Notion.ts              // Notion data source using LlamaIndex
|		|-- Pdf.ts                // Pdf data source using LlamaIndex
|	|-- llms/
|		|-- providers/
|			|-- openrouter.ts    // open router as a llm provider
|			|-- openai.ts	     // open ai as a llm provider
| 			|-- antrhopic.ts    // antrhopic as a llm provider
|		|-- prompting.ts        // create a prompt with returned context
|-- api/
|   |-- chat.ts				   // Edge function to chat 
|-- webhooks/
|   |-- jiraWebhook.ts          // Edge function for Jira Webhook
|   |-- notionWebhook.ts       // Edge function for Notion Webhook
|-- services/
|   |-- JiraService.ts         // Service to jira webhook logic
|	|-- NotionService.ts       // Service to handle notion webhook logic
|	|-- ChatService.ts  	  // Service to handle chat related logic
|-- utils/
    |-- supabaseClient.ts         // Initializes and exports the Supabase client
    |-- llamaIndex.ts.           // Initializes and exports the LlamaIndex client
```

### Domain Layer (`src/domain/`)


#### Embeddings


-   `Embedding.ts`: The  `Embedding`  entity encapsulating the text embeddings data and any domain logic associated with a embedding.
-   `EmbeddingInterface.ts`: An interface defining the contract for data access methods related to text embeddings.
-   `EmbeddingRepository.ts`: The Supabase implementation of  `EmbeddingInterface`, responsible for actual data operations.

### API Layer (`src/api/`)

- `chat.ts`: A Supabase Edge function that acts as an API end point for chat.

### Webhook Layer (`src/webhooks/`)

-   `jiraWebhook.ts`: A Supabase Edge Function that acts as an API endpoint for jira webhook.
-   `notionWebhook.ts`: A Supabase Edge Function that acts as an API endpoint for notion webhook.

### Data Sources (`src/data_sources`)

- `Jira.ts`: Jira data source using LlamaIndex.
- `Notion.ts`: Notion data source using LlamaIndex.
- `Pdf.ts`: Pdf data source using LlamaIndex

### Services Layer (`src/services/`)


-   `JiraService.ts`: Encapsulates the business logic for managing jira related stuff.
- `NotionService.ts`: Encapsulated the business logic for managing notion related stuff.
- `ChatService.ts`: Encapsulated the business logic for managing chat.

### Utils (`src/utils/`)

-   `supabaseClient.ts`: Provides the initialized Supabase client, which is used throughout the application to interact with Supabase services.
- `llamaIndex.ts`: Provides the initialized LlamaIndex client, which is used througout the application.

## Core Concepts

### Domain-Driven Design (DDD)

DDD focuses on aligning the software design closely with the business domain. By structuring the software around the business domain, developers and domain experts can communicate more effectively, and the software becomes more flexible to accommodate future business changes.

### Object-Oriented Programming (OOP)

OOP is a programming paradigm that organizes software design around data, or objects, rather than functions and logic. An object can be defined as a data field that has unique attributes and behavior.

### Interface

In OOP, an interface is a defined contract that specifies a set of methods a class must implement. Interfaces promote loose coupling and allow for more flexible and maintainable code by defining a clear separation between the specification and the implementation.

### Repository

The repository pattern is a commonly used pattern in DDD that abstracts the data persistence layer. It provides a collection-like interface for accessing domain entities, allowing the domain layer to remain agnostic of the underlying data access strategy.
