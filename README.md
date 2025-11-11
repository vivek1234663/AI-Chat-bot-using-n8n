# n8n AI Chatbot Workflow

This project defines an n8n workflow that creates a simple AI-powered
chatbot using: - Google Gemini Chat Model - LangChain AI Agent - Memory
buffer for conversation context - Webhook input/output

## How It Works

1.  **Webhook Node**
    -   Listens at: `/webhook/dcb4a314-9447-457a-b2ae-04eba9f49209`
    -   Receives POST requests from your chatbot UI.
2.  **Google Gemini Chat Model**
    -   Provides LLM capabilities using Google Gemini (PaLM) API.
    -   Connected as the language model for the AI Agent.
3.  **Simple Memory**
    -   Stores the last 100 tokens of conversation history.
    -   Connected to the AI Agent to maintain context.
4.  **AI Agent**
    -   Receives the webhook message.
    -   Uses memory + Gemini to generate a contextual reply.
5.  **Respond to Webhook**
    -   Sends the AI-generated reply back to the UI.

## Purpose

This workflow powers a simple chat interface that sends user messages to
n8n, processes them using AI, and returns a chat response with memory
support.

## Endpoint

POST messages to:

    http://localhost:5678/webhook/dcb4a314-9447-457a-b2ae-04eba9f49209

Payload format:

``` json
{
  "message": "Hello"
}
```

## Output

The workflow returns a JSON response containing the AI reply:

``` json
{
  "reply": "AI response text here"
}
```

## Files

-   `My workflow 5.json` --- the exported n8n workflow
-   `README.md` --- this documentation
