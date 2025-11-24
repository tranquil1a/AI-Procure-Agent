n8n (Webhook)
    ↓
FastAPI (/analyze)
    ↓
PDF/Text Extractor → чистый текст
    ↓
LLM (Llama3/Mistral) → JSON параметры
    ↓
Risk Engine (правила + модели)
    ↓
Supplier Matching (embeddings + cosine similarity)
    ↓
Report Generator (HTML/PDF/JSON)
    ↓
UI (Streamlit) / n8n Output

🟦 1. Data Layer (Данные)

Источники: госзакупки   https://egov.kz/cms/en/articles/economics/procurement_portal
Kaggle                  https://www.kaggle.com/datasets/shivamb/government-procurement-dataset?utm_source=chatgpt.com   
синтетика               https://www.globalpublicprocurementdata.org/gppd/
Хранение: CSV / SQLite
Формат тендера стандартизируется до:
subject, price, deadlines, requirements, customer

🟥 2. NLP/ML Layer

Модули:
LLM Extractor — извлекает параметры → JSON
Risk Analyzer — правила аномалий, сроки, аффилированность
Supplier Matcher — Sentence-Transformers + FAISS

🟩 3. AI-Agent Layer

Функции агента:
принимает тендер
извлекает параметры
анализирует риски
находит поставщиков
формирует отчет

🖥 4. Output Layer

Web UI (Streamlit)
PDF/HTML отчёт
JSON API ответ
вывод в n8n

📦 Структура проекта
/data          — датасеты, тендеры
/ml            — модели, промпты, риск-правила
/backend       — FastAPI
/ui            — интерфейс
/docs          — документация
