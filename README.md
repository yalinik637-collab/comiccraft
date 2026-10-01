# ComicCraft - AI Comic Story Creator

FastAPI + Gemini (Flash for the outline, Pro for the story) + Stable Diffusion (panels) + FPDF2 (PDF export).

## Run in VS Code
1. Open this folder in VS Code (`File > Open Folder`).
2. Open a terminal (`Ctrl+``) and create the environment:
   ```
   python -m venv env
   env\Scripts\activate          # Windows
   source env/bin/activate       # macOS / Linux
   pip install -r requirements.txt
   ```
3. Select the interpreter: `Ctrl+Shift+P` > **Python: Select Interpreter** > `env`.
4. Copy `.env.example` to `.env` and paste your `GEMINI_API_KEY`.
5. Press **F5** (uses `.vscode/launch.json`) or run `uvicorn app.main:app --reload`.
6. Visit http://127.0.0.1:8000 (API docs at `/docs`).

## Modes
- No `GEMINI_API_KEY`: demo text so you can test the whole flow offline.
- `IMAGE_MODE=placeholder` (default): instant demo art. Set `IMAGE_MODE=sd` and install
  `torch diffusers transformers accelerate` for real Stable Diffusion (slow on CPU, fast on GPU).
- Model names live in `.env`. The PDF names `gemini-1.5-*`, which Google has retired, so the defaults are `gemini-2.5-flash` / `gemini-2.5-pro`.

## Structure
`app/` routes, Gemini, image, layout and PDF modules - `templates/` Jinja2 pages - `static/` CSS, panels, exports.

Edit the team section in `templates/index.html`.
