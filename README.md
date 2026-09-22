# Zero-Overhead Context Modeling via Causal Mamba for High-Fidelity FD-NAC — Audio samples

Listening samples and spectrograms for the ICASSP 2027 submission.
Compares Reference / FDK-AAC (LC) / TD-NAC / Proposed at 48 kbps.

**Demo page:** https://seorim0.github.io/fdnac-mamba-demo/

## Folder layout

```
index.html                 the page (edit only the CONFIG block at the bottom)
make_spectrograms.py       audio/**/*.wav  ->  spec/**/*.png
audio/<clip>/reference.wav
audio/<clip>/fdk-aac_48.wav
audio/<clip>/td-nac_48.wav
audio/<clip>/proposed_48.wav
spec/<clip>/<same names>.png
```

`<clip>` is a short folder-safe id (e.g. `es01`). The display name lives in `index.html`.

## Adding clips

1. Drop the 4 WAV files for a clip into `audio/<clip>/` using the names above.
2. Run `python make_spectrograms.py` (needs `librosa matplotlib soundfile`).
3. Add one line to `CONFIG.clips` in `index.html`:
   ```js
   { id: "es01", name: "es01", note: "Speech" },
   ```

Keep clips short (≈8–10 s). 4 files × 44.1 kHz 16-bit stereo ≈ 7 MB per 10 s clip; GitHub Pages sites should stay under 1 GB and individual files under 100 MB.

## Publishing on GitHub Pages

1. Create a public repository under `seorim0` (this README assumes `fdnac-mamba-demo`).
2. Push these files to the `main` branch.
3. Repository → **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`. Save.
4. After a minute the site is live at `https://seorim0.github.io/fdnac-mamba-demo/`.
   Put that URL in the paper in place of `https://github.com/username/repository`.

Test locally before pushing (opening `index.html` directly may block audio in some browsers):

```
python -m http.server 8000
# open http://localhost:8000
```
