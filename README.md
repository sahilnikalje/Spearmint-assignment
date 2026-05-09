# Spearmint-assignment

A full-stack product discovery app where users can browse products or use natural language to ask AI for recommendations.

🌐 **Live Demo**  
Frontend: https://spearmint-assignment-blush.vercel.app/
Backend API: https://spearmint-assignment-9lps.onrender.com  

---

## Tech Stack

- **Backend:** Node.js, Express  
- **Frontend:** React (Vite)  
- **AI/LLM:** Groq API (llama-3.1-8b-instant)  
- **Styling:** CSS  
- **Deployment:** Vercel (Frontend), Render (Backend)

---

## Project Structure

```
DscoverAi-assignment/
├── Backend/
│   ├── controllers/
│   │   ├── productController.js
│   │   └── askController.js
│   │
│   ├── routes/
│   │   ├── productRoutes.js
│   │   └── askRoutes.js
│   │
│   ├── data/
│   │   └── products.js
│   │
│   ├── server.js
│   └── .env
│
└── Frontend/
    ├── src/
    │   ├── components/
    │   │   ├── ProductCard.jsx
    │   │   ├── ProductCard.css
    │   │   ├── SearchBar.jsx
    │   │   └── SearchBar.css
    │   │
    │   └── App.jsx
    │
    ├── App.css
    └── vite.config.js
```

---

## How to Run Locally

### Step 1 – Get a Free Groq API Key

1. Go to https://console.groq.com  
2. Sign up  
3. Create a new API key  
4. Copy the key  

---

### Step 2 – Run the Backend

```bash
cd Backend
npm install
```

Create a `.env` file inside the Backend folder:

```
GROQ_API_KEY=your_key_here
PORT=3000
VITE_URI=http://localhost:5173
```

Start the server:

```bash
node server.js
```

Server runs on:

```
http://localhost:3000
```

---

### Step 3 – Run the Frontend (Vite)

```bash
cd Frontend
npm install
```

Create a `.env` file inside the Frontend folder:

```
VITE_API_URI=http://localhost:3000
```

Start frontend:

```bash
npm run dev
```

App runs on:

```
http://localhost:5173
```

---

## API Endpoints

### GET /api/products

Returns all products.

Supports optional category filter:

Example:
```
/api/products?category=electronics
```

---

### POST /api/ask

Accepts a natural language query and returns AI-matched products.

Request Body:

```json
{
  "query": "budget laptop for student"
}
```

Response:

```json
{
  "products": [...],
  "summary": "Found budget-friendly laptops suited for students"
}
```

---

## How the AI Ask Flow Works

1. User enters a natural language query.
2. Frontend sends POST request to `/api/ask`.
3. Backend:
   - Builds formatted product list string.
   - Sends structured prompt to Groq LLM.
4. LLM returns:
   - Matching product IDs
   - Short explanation summary
5. Backend filters products using returned IDs.
6. Frontend displays:
   - Highlighted matching products
   - AI summary
   - Loading and error states

---

## What’s Implemented

- In-memory product catalog
- REST API with:
  - GET /api/products
  - POST /api/ask
- LLM integration via Groq
- Structured JSON response parsing
- Error handling for failed LLM calls (502 response)
- React (Vite) frontend with:
  - useState
  - useEffect
  - Reusable components
- Product highlighting for AI results
- Loading spinner during AI processing
- Clean UI with ₹ price formatting

---

## Deployment

Frontend deployed on **Vercel**  
Backend deployed on **Render**

Production API Base:
```
https://spearmint-assignment-9lps.onrender.com
```

Production App:
```
https://discvrai-assignment.vercel.app
```

---

## Time Spent
3.5hr
