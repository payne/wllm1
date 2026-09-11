# wllm1 — LARC VEC Assistant (Web-LLM Demo)

An in-browser AI assistant for the [Laurel Amateur Radio Club VEC](https://larc-vec.org) — ask questions about becoming a Volunteer Examiner, exam session rules, FCC fees, and policies.

Powered by [@mlc-ai/web-llm](https://github.com/mlc-ai/web-llm). The AI model runs **entirely in your browser** — no server, no API keys.

## Live Demo

Open `index.html` in a browser, or serve the repo with any static file server:

```bash
npx serve .
# then open http://localhost:3000
```

Or deploy to GitHub Pages: Settings → Pages → branch `main`, root `/`.

## Browser Requirements

WebGPU is required to run the model:

| Browser | Supported |
|---|---|
| Chrome 113+ / Edge 113+ | ✅ Yes |
| Safari 18+ (macOS / iOS 18+) | ✅ Yes (with WebGPU flag enabled) |
| Firefox | ❌ No WebGPU yet |

**iPhone/Safari:** Settings → Safari → Advanced → Feature Flags → enable **WebGPU**.

## First Load

The app now chooses a model based on the device:

- Desktops/laptops try `Llama-3.2-3B-Instruct-q4f16_1`
- Smaller or Safari/mobile devices fall back to smaller models automatically

The chosen model is downloaded from the MLC CDN on first use and cached in the browser. Subsequent loads are much faster.

## Troubleshooting

If a model still fails to load, the app now shows:

- which model it tried
- the browser-reported device memory (when available)
- WebGPU adapter limits (when available)
- a likely cause when the failure looks memory-related

For the best results, use current Chrome or Edge on a desktop/laptop with WebGPU enabled.

## Data Source

Content is from [`larc-vec.org/becomeve.php`](https://larc-vec.org/becomeve.php), stored in `data.js`.
Topics covered:
- What is the Laurel VEC
- VE qualifications & how to become a VE
- Code of conduct (no fees, no discrimination)
- Team Leader responsibilities
- Exam session flow & retesting policy
- FCC $35 application fee rules
- Online/remote exam policy