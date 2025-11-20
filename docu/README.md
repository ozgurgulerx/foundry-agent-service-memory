# Documentation and notebook plan

This repository will host notebooks that demonstrate how to build Azure AI Agent
Service experiences (with the agent-framework) and plain Azure OpenAI apps
using the Responses API.

## Folders
- `notebooks/`: Jupyter notebooks for hands-on guides.
- `docu/`: Documentation, plans, and supporting notes.

## Prerequisites
- Azure subscription with an Azure OpenAI resource that supports the Responses API.
- Access to Azure AI Agent Service (preview) and any required preview features.
- Python 3.11+ environment with `pip`.
- API credentials stored as environment variables (example names below; adjust to your setup):
  - `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_API_VERSION` (defaults to `2024-02-15-preview` in notebooks).
  - `AZURE_OPENAI_RESPONSES_DEPLOYMENT_NAME` (Responses deployment for `AzureOpenAIResponsesClient`).
  - Optional: `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME`, `AZURE_OPENAI_BASE_URL`.
  - `AZURE_AGENT_SERVICE_ENDPOINT`, `AZURE_AGENT_SERVICE_API_KEY` (if using key auth), or configuration for AAD auth if preferred.

## Suggested notebooks
- `00_env_setup.ipynb`: Create/activate the virtual environment, install dependencies, and verify connectivity to Azure OpenAI and Agent Service.
- `01_responses_api_basics.ipynb`: Call the Responses API (chat-style prompts), control temperature/stop sequences, and capture reasons codes.
- `02_responses_structured_outputs.ipynb`: Structured outputs, JSON/object mode, and lightweight tool use via the Responses API.
- `03_agent_framework_baseline.ipynb`: Minimal agent-framework walkthrough (tools, steps, and simple memory) running locally.
- `04_agent_service_tools_and_memory.ipynb`: Push an agent to Azure AI Agent Service, wire tools, handle long-running operations, and store/reuse conversation memory.
- `05_llm_app_patterns.ipynb`: Build a small LLM app that mixes Responses API calls with agent-service calls (e.g., routing/query rewriting) and capture logging/telemetry.

## Quick start (local, WIP)
1) Create a virtual environment: `python -m venv .venv && source .venv/bin/activate` (or `.\.venv\Scripts\activate` on Windows).
2) Upgrade pip and install base deps: `pip install -U pip -r requirements.txt`
   - Requirements include `agent-framework-azure-ai==1.0.0b251114` (preview). Add any Agent Service SDK once the version is chosen.
3) Populate the environment variables listed above (e.g., via `.env` or your shell) and run `jupyter lab` or `jupyter notebook`.

## Notes and open items
- Confirm which agent-framework SDK version to pin for the Agent Service notebooks.
- Decide on the storage/memory provider for conversation transcripts (Table Storage, Cosmos DB, or blob) and wire it into the relevant notebook.
- Add monitoring/observability guidance once deployment flow is stable.
