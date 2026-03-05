# 𐤀 NUMID.AI

> *Ancient languages, future minds.*

A futuristic AI-powered translation platform that bridges 5,000 years of human writing — from Sumerian cuneiform to Phoenician abjad, Egyptian hieroglyphs to Old Norse runes — powered by **Anthropic Claude**.

---

## ✨ What It Does

Numid.ai translates modern text into 17 ancient and classical writing systems, rendering authentic Unicode scripts with:

- **Authentic script rendering** — real Unicode characters for each writing system
- **Phonetic transliteration** — IPA and scholarly romanization
- **Word-by-word breakdown** — sign-by-sign analysis
- **Cultural & historical context** — why certain words/signs were chosen
- **Pronunciation guide** — how ancient peoples would have sounded
- **Confidence ratings** — honest about reconstructed languages
- **Cross-language comparison** — same phrase in 6 scripts simultaneously
- **Historical timeline** — visual journey through 5,000 years of writing

---

## 🗿 Supported Ancient Languages (17)

| Language | Era | Script | Direction |
|---|---|---|---|
| **Phoenician** | 1050–150 BCE | Phoenician Abjad | RTL |
| **Sumerian** | 3500–2000 BCE | Cuneiform | LTR |
| **Akkadian** | 2800–100 BCE | Cuneiform | LTR |
| **Ancient Egyptian** | 3200 BCE–4th c CE | Hieroglyphics | RTL |
| **Proto-Sinaitic** | 1900–1500 BCE | Pictographic | RTL |
| **Ugaritic** | 1400–1185 BCE | Cuneiform Alphabet | LTR |
| **Imperial Aramaic** | 800 BCE–600 CE | Aramaic Abjad | RTL |
| **Old Persian** | 600–300 BCE | Cuneiform | LTR |
| **Linear B** | 1450–1200 BCE | Syllabary | LTR |
| **Gothic** | 350–800 CE | Gothic Alphabet | LTR |
| **Etruscan** | 700–100 BCE | Old Italic | RTL |
| **Classic Maya** | 250–900 CE | Maya Glyphs | LTR |
| **Vedic Sanskrit** | 1500–200 BCE | Brahmi | LTR |
| **Classical Latin** | 75 BCE–600 CE | Roman | LTR |
| **Ancient Greek** | 800–300 BCE | Greek | LTR |
| **Old Norse** | 800–1300 CE | Runes | LTR |
| **Coptic** | 200–17th c CE | Coptic | LTR |

---

## 🗂️ Repository Structure

```
numid-ai/
│
├── backend/                        # Python FastAPI server
│   ├── main.py                     # App entry point, CORS, routes mounting
│   ├── requirements.txt            # Python dependencies
│   ├── __init__.py
│   │
│   ├── models/
│   │   ├── __init__.py
│   │   └── languages.py            # Full language catalogue (17 languages)
│   │
│   ├── routers/
│   │   ├── __init__.py
│   │   └── translate.py            # All API endpoints
│   │
│   ├── services/
│   │   ├── __init__.py
│   │   ├── translator.py           # Anthropic Claude translation engine
│   │   └── audio.py                # TTS pronunciation generation
│   │
│   └── utils/
│       └── __init__.py
│
├── frontend/                       # React application
│   ├── package.json
│   ├── public/
│   │   └── index.html
│   └── src/
│       ├── index.js                # React entry point
│       ├── App.jsx                 # Root component, nav, star field
│       │
│       ├── pages/
│       │   ├── TranslatorPage.jsx  # Main translation UI
│       │   ├── TimelinePage.jsx    # Historical language timeline
│       │   └── ComparePage.jsx     # Multi-language comparison
│       │
│       ├── components/
│       │   ├── LanguageCard.jsx    # Individual language selector card
│       │   └── TranslationResult.jsx # Full translation display
│       │
│       ├── hooks/
│       │   └── useTranslation.js   # API hooks (languages, translate, compare)
│       │
│       └── styles/
│           └── globals.css         # Design system, variables, animations
│
├── docs/                           # Documentation
│
├── .env                            # Your config (not committed)
├── .env.example                    # Template
├── .gitignore
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites
- Python 3.10+
- Node.js 18+
- An **Anthropic API key** from [console.anthropic.com](https://console.anthropic.com)

### 1. Setup

```bash
unzip numid-ai.zip
cd numid-ai
cp .env.example .env
```

Edit `.env` and set your `ANTHROPIC_API_KEY`.

### 2. Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate       # Windows: venv\Scripts\activate
pip install -r requirements.txt
cd ..
python -m backend.main
# → API running at http://localhost:8000
# → Docs at http://localhost:8000/docs
```

### 3. Frontend

```bash
cd frontend
npm install
npm start
# → App at http://localhost:3000
```

---

## 🔌 API Reference

### `GET /api/v1/languages`
Returns all 17 languages with full metadata.

### `POST /api/v1/translate`
```json
{
  "text": "The stars are eternal",
  "target_language_id": "phoenician",
  "source_language": "auto",
  "style": "formal"
}
```
**style options:** `formal` | `poetic` | `conversational` | `inscription`

### `POST /api/v1/compare`
```json
{
  "text": "I am the king",
  "language_ids": ["sumerian", "ancient_egyptian", "phoenician"]
}
```

### `POST /api/v1/pronunciation`
```json
{
  "script_text": "𐤁𐤏𐤋",
  "language_id": "phoenician"
}
```

### `GET /api/v1/timeline`
Languages grouped by historical era.

---

## ⚙️ Environment Variables

| Variable | Required | Description |
|---|---|---|
| `ANTHROPIC_API_KEY` | ✅ | Powers all translations via Claude |
| `HOST` | no | Backend host (default `0.0.0.0`) |
| `PORT` | no | Backend port (default `8000`) |
| `DEBUG` | no | Hot reload in development |
| `TTS_PROVIDER` | no | `offline` or `google` for audio |
| `GOOGLE_TTS_API_KEY` | no | Enhanced audio pronunciation |
| `MAX_TOKENS_PER_REQUEST` | no | Claude token limit (default 4096) |

---

## 🧠 How the AI Translation Works

1. **System prompt** instructs Claude as an expert in all 17 ancient language systems
2. Claude translates the modern text, choosing appropriate signs/letters
3. Returns structured JSON: script rendering, IPA, word breakdown, cultural notes
4. For extinct/reconstructed languages, Claude is honest about confidence level
5. Responses are **cached** (1 hour) to minimize API calls
6. Parallel translation available for cross-language comparison

---

## 🏛️ Philosophy

> "Every alphabet you know descends from Phoenician merchants scratching consonants
> onto clay in 1050 BCE. Every number you write traces to Sumerian accountants in Ur.
> We don't start from scratch — we stand on 5,000 years of human ingenuity."
>
> — Numid.ai

---

## 📝 License

MIT — free to use, fork, and build upon. If you build something cool, share it.
