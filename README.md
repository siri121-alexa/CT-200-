CT-200 QA SYSTEM 

A FastAPI-based backend application that converts a technical document into a structured, versioned tree and generates QA test case ideas while maintaining traceability across document versions.

---

 Features

-  Upload technical documents (.txt)
-  Parse documents into a hierarchical section tree
-  Document versioning
-  Browse document structure
-  Generate QA test case ideas for selected sections
- Maintain traceability between document sections and generated test cases
-  Interactive Swagger API documentation

---

 Tech Stack

- Python 3.10+
- FastAPI
- Pydantic
- Uvicorn

---
Project Structure

```
project/
│── main.py
│── requirements.txt
│── README.md
```

---

⚙ Installation

Clone the repository

```bash
git clone <repository-url>
cd project
```

Install dependencies

```bash
pip install -r requirements.txt
```

or

```bash
pip install fastapi uvicorn python-multipart
```

---

 Running the Application

```bash
uvicorn main:app --reload
```

The server starts at

```
http://127.0.0.1:8000
```

---

 API Documentation

Swagger UI

```
http://127.0.0.1:8000/docs
```

ReDoc

```
http://127.0.0.1:8000/redoc
```

---

## 🚀 API Endpoints

### Upload Document

```
POST /upload
```

Uploads a technical document and creates Version 1.

---

List Documents

```
GET /documents
```

Returns all uploaded documents.

---

Get Document Tree

```
GET /tree/{document_name}
```

Returns the structured hierarchy of sections.

---

 Get Versions

```
GET /versions/{document_name}
```

Returns available document versions.

---

 Generate QA Test Cases

```
POST /generate/{document_name}/{section_id}
```

Generates QA test-case ideas for the selected section.

---

View Traceability

```
GET /trace/{section_id}
```

Displays the mapping between document sections and generated test cases.

---

 Sample Input

```text
 Device Overview
CardioTrack CT-200 measures systolic and diastolic blood pressure.

Safety
Do not use while charging.

 Battery
Uses four AA batteries.

Display
Displays blood pressure and pulse rate.

 Bluetooth
Synchronizes readings with the mobile application.
```

---

 Example Response

```json
{
  "document": "CardioTrack.txt",
  "version": 1,
  "total_sections": 6
}
```

---


Each uploaded document is stored as a new version. Every section contains version information, allowing traceability to remain valid even after updates.

---


Each generated test case is linked to its originating section, making it easy to identify which requirements are covered.

Example:

```
Safety Section
        │
        ├── Test Case 1
        ├── Test Case 2
        └── Test Case 3
```

---
 Future Enhancements

- PDF and DOCX support
- Markdown parsing
- Database integration (PostgreSQL/MongoDB)
- AI-powered test case generation
- Authentication & Authorization
- Document comparison and diff visualization
- Export test cases to Excel/PDF

---

## 👨‍💻 Author

Developed as a backend assignment using **Python** and **FastAPI**.
