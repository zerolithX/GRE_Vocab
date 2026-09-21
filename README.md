# Vocab Mountain

A personal vocabulary-learning Android app built from your 960-word list (32 groups).
Each word gets a related photo (fetched live, no API key needed) and a looked-up
dictionary meaning on tap. Includes a "match the picture to the word" quiz mode,
starring, and per-word "learned" tracking (saved on-device).

## How to get the APK

1. Create a new **public or private GitHub repo** and push everything in this folder to it
   (keep the folder structure exactly as is — the `.github/workflows/build-apk.yml`
   file must stay at that path).

   ```bash
   git init
   git add .
   git commit -m "Vocab Mountain app"
   git branch -M main
   git remote add origin <your-repo-url>
   git push -u origin main
   ```

2. On GitHub, go to the **Actions** tab of your repo. The "Build Android APK" workflow
   runs automatically on every push to `main` (or click "Run workflow" to trigger it
   manually).

3. When the run finishes (a few minutes), open it and download the
   **vocab-mountain-debug-apk** artifact — that's your installable `app-debug.apk`.

4. Transfer the APK to your Android phone and install it (you'll need to allow
   "install from unknown sources" for debug builds — this is normal for a personal app).

## What's inside

- `www/index.html` — the whole app (Material-style UI, word list, quiz, progress).
- `www/vocab.json` — your 960 words, grouped exactly as in your vocab sheet.
- `resources/icon.png` — your uploaded icon; the workflow auto-generates all the
  Android launcher icon sizes from it.
- `capacitor.config.json` / `package.json` — Capacitor project setup.
- `.github/workflows/build-apk.yml` — the CI pipeline that turns the web app into
  a signed-debug `.apk` using Capacitor + Gradle, no local Android Studio needed.

## Notes

- Photos and dictionary definitions are fetched live from free public sources
  (loremflickr.com and dictionaryapi.dev) — the phone needs internet the first
  time it loads a word's photo/meaning.
- Starred words and "learned" marks are stored locally on the device (`localStorage`),
  so they persist between app opens but aren't backed up anywhere else.
- Want a release (signed, Play-Store-ready) build instead of debug? Say the word —
  it just needs a signing keystore added as a GitHub secret and one more workflow step.
