# n8n Workflow Automation Projects 🚀

Welcome to my portfolio of n8n workflow automation projects! During my internship as an n8n Workflow Automation Developer, I designed and implemented three robust, AI-powered automation workflows. These projects solve real-world business problems by integrating APIs, AI agents, and data management systems to eliminate manual effort and scale operations.

This repository contains the exported JSON workflows for the following three projects:

---

## 1. 📧 Automated Email Invoice Parsing and Data Entry Workflow
**File:** `Email Invoice.json`

### Overview
This workflow automates the tedious process of extracting invoice information from emails and logging it into a database, removing the need for manual data entry.

### ⚙️ How It Works:
1. **Trigger:** Listens for new emails via the **Gmail Trigger**.
2. **Filter & Fetch:** Filters emails for invoices and downloads the associated PDF attachments from Google Drive.
3. **Extraction & AI Parsing:** Extracts raw text from the PDF and passes it to the **Google Gemini Chat Model** via an LLM Chain to intelligently parse out the `invoice_name`, `company_name`, `total_invoice_amount`, and `line_items`.
4. **Data Entry:** Automatically creates new records in an **Airtable** "Invoice" database and loops through every individual line item to log them into a related "Invoice Line Items" table.

### 🛠️ Key Nodes Used:
- Gmail Trigger & Node
- Google Drive (Download & Upload Binary Data)
- Extract From File (PDF to text)
- LangChain / Google Gemini (Structured Output Parser)
- Airtable Integration
- Split In Batches (Loop Over Items)

---

## 2. 📈 Technical Analysis (TA) Telegram Bot
**File:** `TA_Get___Analyze_Chart.json`

### Overview
A conversational, AI-driven Telegram bot built for retail and institutional traders. Users can request a specific stock ticker, and the bot will fetch the chart, conduct a full technical analysis using a vision model, and format a professional response with actionable insights.

### ⚙️ How It Works:
1. **Trigger:** Listens for user messages on Telegram (e.g., "Can you analyze AAPL?").
2. **AI Agent & Memory:** Uses an **Azure OpenAI Agent (GPT-4o/mini)** with Window Buffer Memory to maintain context and conversation history.
3. **Tool Call (GetChart):** When a user asks for analysis on a ticker, the AI calls a sub-workflow/tool to ping `chart-img.com` for an advanced TradingView chart (including Volume Profile and MACD).
4. **Vision Analysis:** The downloaded chart is sent to a Vision AI (**Llama 3.2 11B Vision** or GPT-4o) which analyzes Candlesticks, Volume, MACD, and Support/Resistance levels.
5. **Delivery:** The chatbot formats the complex technical analysis into readable Markdown and sends the detailed analysis—along with the actual chart image inline—back to the user on Telegram.

### 🛠️ Key Nodes Used:
- Telegram Trigger & Action Nodes
- LangChain Agents (Azure OpenAI GPT-4o / GPT-4o-mini)
- Memory Buffer Window
- HTTP Request (Chart Generation API)
- Vision Model (Llama 3.2 Vision)
- Tool Workflow

---

## 3. ✍️ AI SEO Keyword Research & Blog Writing Automation
**File:** `SEO KeyWord research and writing.json`

### Overview
A fully autonomous content generation engine that researches top-ranking search engine results, extracts factual data, writes an SEO-optimized blog post, and humanizes the tone before publishing it securely to the cloud.

### ⚙️ How It Works:
1. **Form Trigger:** Takes a "Main Keyword" input (e.g., "How to be profitable in crypto trading") and the number of SERP websites to parse.
2. **SEO Keyword Generation:** An AI Agent discovers real-time trending sub-topics and generates 5-7 highly relevant short and long-tail SEO keywords. These are automatically appended to a **Google Sheet**.
3. **Web Scraping:** Uses **ScraperAPI** to fetch and scrape the top-ranking web pages for the target keyword, stripping out ads and scripts to get clean text.
4. **Blog Composition:** The **SEO Content Writer AI Agent** analyzes the scraped text, identifies knowledge gaps, and drafts a superior, in-depth blog article optimized for search engines.
5. **Humanizing the Output:** The drafted text is passed to a second AI Agent that revises the tone to be conversational, empathetic, and naturally engaging—removing any "AI-sounding" jargon.
6. **Formatting & Saving:** The final content is wrapped into clean semantic HTML and automatically uploaded to a specific **Google Drive** folder.

### 🛠️ Key Nodes Used:
- Form Trigger
- HTTP Request (ScraperAPI)
- LangChain Agents (Azure OpenAI GPT-4o & GPT-4o-mini)
- LangChain Structured Output Parsers
- Google Drive & Google Sheets Integration
- Split In Batches / Iteration

---

## 🚀 Setup Instructions
To run these workflows in your own n8n instance:
1. Open your n8n dashboard.
2. Click on **Add Workflow** -> **Import from File**.
3. Select any of the JSON files from this project.
4. Update the **Credentials** for the respective nodes (e.g., Google OAuth, Telegram Bot Token, Azure OpenAI keys, Airtable PAT).
5. Activate the workflow!

## 💡 Skills Demonstrated
- **AI/LLM Orchestration:** Designing multi-agent systems, vision models, and using Structured Output Parsers.
- **Data Pipelines:** Parsing binary data (PDF extraction), Web Scraping, and structured database injection.
- **API Integration:** Seamlessly integrating with Google Workspace, Airtable, Telegram, and 3rd party APIs (ScraperAPI, Chart-Img).
- **Workflow Architecture:** Building robust sub-workflows, iterating over batched items, and utilizing conditional flows.
