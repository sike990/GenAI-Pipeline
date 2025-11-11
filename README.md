# GenAI LaTeX Resume Writer

_Automatically generate a custom LaTeX resume for any job posting using generative AI, RAG, and your project portfolio._

---

## 🚀 Features

- **Streamlit Web UI:** Clean interface to input a job posting URL.
- **Web Scraping:** Fetches job description via the provided URL with WebBaseLoader.
- **Text Cleaning:** Processes HTML, removes URLs, whitespace, and extraneous tags.
- **LLM-Powered Job Extraction:** Uses Groq's llama-3.1-70b-versatile for parsing and extracting the job's requirements.
- **RAG Pipeline:**
  - **Vector Store:** User project portfolio loaded from CSV, vectorized using ChromaDB.
  - **Skill Matching:** Finds and ranks projects most relevant to job requirements.
  - **Generative Resume Output:** Synthesizes a tailored LaTeX resume aligning your skills/projects to the job.

---

## 🛠️ How It Works

1. **User Input:** Paste the job posting URL into the Streamlit app, click "Submit".
2. **Fetch & Clean:** Job description fetched and cleaned (`utils.py`).
3. **Load Portfolio:** Your project data (`app/resource/my_portfolio.csv`) is loaded into ChromaDB and vectorized by tech stack.
4. **Extract Job Details:** LLM parses the cleaned job description and returns structured JSON with job role, skills, and requirements.
5. **Query Portfolio (RAG):** Portfolio projects are ranked by relevance to the job's required skills.
6. **Generate Resume:** LLM draft of LaTeX resume matching your experience with the job; displayed in the app.

---

## 🔧 Setup & Installation

1. **Clone the Repository:**
    ```bash
    git clone https://github.com/sike990/genai-pipeline.git
    cd genai-pipeline
    ```

2. **Install Dependencies:**
    Create a `requirements.txt` with:
    ```
    streamlit
    langchain-groq
    langchain-community
    langchain-core
    pandas
    chromadb
    python-dotenv
    ```

    Then install:
    ```bash
    pip install -r requirements.txt
    ```

3. **Create `.env`:**
    ```env
    GROQ_API_KEY='your-groq-api-key-here'
    ```

4. **Prepare Your Portfolio CSV:**
    - Path: `app/resource/my_portfolio.csv`
    - Columns: `Techstack`, `Links`
    - Example:

      | Techstack                               | Links                                                     |
      |-----------------------------------------|-----------------------------------------------------------|
      | Python Django REST Framework SQL        | [https://github.com/your-username/my-django-api](https://github.com/your-username/my-django-api)     |
      | React Typescript AWS Lambda CI/CD       | [https://github.com/your-username/my-serverless-app](https://github.com/your-username/my-serverless-app) |
      | Data Analysis Pandas Numpy Matplotlib   | [https://github.com/your-username/data-science-report](https://github.com/your-username/data-science-report) |
      | Java Spring Boot Microservices          | [https://github.com/your-username/ecommerce-backend](https://github.com/your-username/ecommerce-backend)     |

---

## 🏃‍♂️ Running the App

1. Ensure `.env` and `my_portfolio.csv` are set up correctly.
2. Launch Streamlit:

    ```bash
    streamlit run main.py
    ```

3. Open your browser to the local URL (e.g., http://localhost:8501) to start.

---

## 🔮 Future Improvements

- **PDF Job Description:** Allow uploading PDF job descriptions; integrate PDF parsing (e.g., via `pypdf`).
- **Portfolio Upload:** Enable uploading custom portfolio CSV or resume (PDF/DOCX) in-app.
- **Profile Input:** Streamlit UI fields for name, contact info, summary; used to enrich resume content.
- **Template Selection:** Choose between multiple LaTeX resume templates (e.g., moderncv, classic, simple article).
- **Cover Letter Generation:** Generate a tailored cover letter matching the resume/job posting.

---

## 📄 License

MIT

---

## ✨ Contributions

Open to PRs and suggestions! See [issues](https://github.com/sike990/genai-pipeline/issues).

---
