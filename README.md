# ⚡ Ghostty Terminal — Tesla Coil Cursor Shader

A sleek **Ghostty** setup featuring a custom **GLSL tesla-coil cursor trail shader** and a frosted-glass window design. Your cursor leaves an electric arc trail behind it as you move — like a tiny lightning bolt every time you navigate.

![Ghostty](https://img.shields.io/badge/Ghostty-Custom%20Shader-7b6cff?style=for-the-badge&logo=ghostty)
![Language](https://img.shields.io/badge/GLSL-Shader-blue?style=for-the-badge)
![Theme](https://img.shields.io/badge/Theme-Catppuccin%20Mocha-cba6f7?style=for-the-badge)

---

## ✨ Showcase

<p align="center">
  <b>Glass Design + Tesla Coil Trail</b>
</p>

<p align="center">
  <img src="/Screenshot 2026-09-27 at 22.59.11.png" alt="Ghostty demo — glass design with tesla coil cursor trail" width="620"/>
</p>

> **Default (red trail)** — shader ships red. Swap the color block to **green** (code below).
<p align="center">
  <b>⚡ Red Shader Variant</b>
</p>

<p align="center">
  <img src="/Red.gif" alt="Ghostty red tesla coil shader" width="420"/>
</p>
---
<p align="center">
  <b>⚡ Green Shader Variant</b>
</p>

<p align="center">
  <img src="/green.gif" alt="Ghostty green tesla coil shader" width="420"/>
</p>

---

## 🎨 Green Shader Color Block

Drop this into the top of `shaders/tesla_coil.glsl` for the **electric green** look:

```glsl
const vec4 TRAIL_COLOR = vec4(0.2, 1.0, 0.2, 1.0); // Green
const vec4 CURRENT_CURSOR_COLOR = TRAIL_COLOR;
const vec4 PREVIOUS_CURSOR_COLOR = TRAIL_COLOR;
const vec4 TRAIL_COLOR_ACCENT = vec4(0.5, 1.0, 0.5, 1.0); // Brighter green
const vec4 ELECTRIC_COLOR = vec4(0.3, 1.0, 0.3, 1.0); // Electric green color
const float GLOW_INTENSITY = 0.3;              // Glow blend intensity (0.0 - 1.0)
```

> Want red (default)? Replace the block with red-channel values, e.g. `vec4(1.0, 0.2, 0.2, 1.0)` for `TRAIL_COLOR`.

---

## 🪟 Glass / Frosted Design

A translucent, blurred macOS titlebar-style window that lets your wallpaper bleed through:

<p align="center">
  <img src="https://img.shields.io/badge/background--opacity-0.7-333?style=for-the-badge">
  <img src="https://img.shields.io/badge/blur-20px-333?style=for-the-badge">
  <img src="https://img.shields.io/badge/titlebar-transparent-333?style=for-the-badge">
</p>

---

## 📁 Repo Structure

```
ghostty/
├── README.md
├── config                  # Ghostty main config
└── shaders/
    └── tesla_coil.glsl     # Custom cursor-trail shader (green variant)
```

---

## ⚙️ Config

```ini
font-size = 12
font-family = JetBrainsMono Nerd Font
background-opacity = 0.7
background-blur = 20
background-blur-radius = 20
mouse-hide-while-typing = true
window-decoration = true
macos-option-as-alt = true
theme = Catppuccin Mocha
copy-on-select = clipboard
macos-titlebar-style = transparent
custom-shader = shaders/tesla_coil.glsl
custom-shader-animation = always
```

---

## 🚀 Install

1. **Copy the shader** into your Ghostty config dir:

   ```bash
   mkdir -p ~/.config/ghostty/shaders
   cp shaders/tesla_coil.glsl ~/.config/ghostty/shaders/
   ```

2. **Link / paste the config** (or add just the relevant lines to your existing `~/.config/ghostty/config`):

   ```bash
   cp config ~/.config/ghostty/config
   ```

3. **Reload Ghostty** — `Cmd + Shift + ,` (or quit & reopen).

4. **Pick your colors** — swap the shader's color block (see [Green Shader Color Block](#-green-shader-color-block)).

---

## 🧪 Tweaking the Effect

The shader exposes knobs at the top of `tesla_coil.glsl` — tweak freely:

| Constant | Effect |
|---|---|
| `DURATION` | Trail lifetime in seconds (`0.8`) |
| `ARC_NOISE_TIME_SCALE` | Arc waviness animation speed |
| `ARC_NOISE_SPACE_SCALE` | Spatial frequency of the noise |
| `ARC_OFFSET_AMPLITUDE` | How wavy the arc is (`0.08`) |
| `BRANCH_TIME_SCALE` | Branch animation speed |
| `BRANCH_FREQUENCY` | Number of branches (`3.0`) |
| `ARC_THICKNESS_BASE` | Base thickness of the arc line |
| `ARC_THICKNESS_PULSE` | Pulsation amount |
| `ARC_PULSE_SPEED` | Thickness pulse speed |
| `ARC_COLOR_PULSE_SPEED` | Color-shift speed |
| `CURSOR_OPACITY` | Cursor transparency (`0.0`–`1.0`) |
| `GLOW_INTENSITY` | Glow blend intensity (`0.0`–`1.0`) |

---

## 📄 License

Personal config — use it however you like. The shader builds on Inigo Quilez's 2D distance functions ([iquilezles.org/articles/distfunctions2D/](https://iquilezles.org/articles/distfunctions2D/)).
