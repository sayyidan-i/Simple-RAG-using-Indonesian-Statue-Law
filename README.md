# Simple RAG UUD 1945 Using LangChain and Gemini API

### Library yang dipakai
- `google-generativeai`: package untuk menggunakan Gemini API [docs](https://pypi.org/project/google-generativeai/)
- `chromadb`: open source vector database
- `pypdf`: untuk ekstrak data dari pdf
- `IPython.display.Markdown`: untuk menampilkan Markdown agar output LLM lebih rapi
- `textwrap`: Mengubah string/teks ke dalam bentuk yang kita butuhkan
- `langchain` and `langchain-community`: Framework untuk men-develop aplikasi menggunakan Large Language Models (LLMs)


### Langkah-langkah secara general

1. Import library yang dibutuhkan
2. inisiasi model menggunakan ChatGoogleGenerativeAI, tentukan model, api, temperature, dll
3. Load PDF menggunakan PyPDFLoader
4. Gabungkan setiap text dari semua pages
5. Potong text ke dalam chunk-chunk, dalam notebook ini digunakan metode Recursive. Tentukan chunk_size dan chunk_overlap. Harapannya, kita chunk data berdasarkan informasi yang relevan
6. Lakukan Text Embeddings, yaitu representasi teks dalam bentuk numeris untuk menangkap informasi semantik dan kontekstual dalam bentuk vektor dimensional. Teks dengan semantik yang mirip akan memiliki representasi vektor yang mirip juga.
7. Simpan text embeddings ke dalam vector database. Dalam kasus ini adalah Chroma
8. Buat chain yang berisi parameter model, retriever (vector index), dan return_source_document
9. Buat question dan lempar ke chain yang telah dibuat sebelumnya untuk mendapatkan respon
10. Dapat pula dibuat dalam bentuk prompt template