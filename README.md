# keyboard-plus-assets

Public CDN for the on-device prediction model assets shipped with the [KeyboardPlus](https://play.google.com/store/apps/details?id=com.themejunky.keyboardplus) Android keyboard.

The app fetches `manifest.json` from this repo's `main` branch, then downloads the per-language model files from the corresponding GitHub Release. Each file is SHA-256 verified after download.

## Layout

- [`manifest.json`](manifest.json) — single source of truth: per-language file URLs, SHA-256 digests, sizes.
- GitHub Releases (`assets-<lang>-v<N>`) host the binary artefacts referenced by the manifest.

## Per-language assets

For each language, four files are published:

| File | Purpose |
|------|---------|
| `<lang>_5gram.binary` | KenLM 5-gram language model (trie format) |
| `<lang>_bpe.model` | SentencePiece BPE tokenizer (binary) |
| `<lang>_bpe.vocab` | SentencePiece BPE vocab (text) |
| `<lang>_transformer.ptl` | PyTorch Mobile INT8-quantised transformer |

## Currently published

| Language | Release | Total |
|----------|---------|-------|
| Romanian (`ro`) | [`assets-ro-v1`](https://github.com/themejunky/keyboard-plus-assets/releases/tag/assets-ro-v1) | ~62 MB |
| Spanish (`es`) | [`assets-es-v1`](https://github.com/themejunky/keyboard-plus-assets/releases/tag/assets-es-v1) | ~104 MB |

## Provenance

Models are trained on a mix of [OpenSubtitles 2018](https://opus.nlpl.eu/OpenSubtitles2018.php) and Wikipedia dumps. Source code for the training pipeline lives in a separate (private) repository. The published artefacts are derivative model weights, not raw corpus data.

## License

The contents of this repository (manifest + model binaries) are released under the [MIT License](LICENSE). Underlying training corpora retain their original licenses (OpenSubtitles: see source; Wikipedia: CC BY-SA 4.0).
