# CobbMeasure — Scoliosis Cobb Angle Measurement Tool

A clean, browser-based clinical tool for measuring the **Cobb angle** on spine radiographs, following the standard method adopted by the **Scoliosis Research Society (SRS)**.

🔗 **Live demo:** `https://<your-username>.github.io/cobb-angle-app/`

---

## Features

| Feature | Details |
|---|---|
| Image loading | Click, drag-and-drop, or paste any JPEG/PNG radiograph |
| Upper end vertebra | 2-click superior endplate line with extended dashed projections |
| Lower end vertebra | 2-click inferior endplate line with extended dashed projections |
| Apical vertebra | 1-click cross-hair marker |
| Cobb angle | Real-time calculation, displayed as arc with numeric label at intersection |
| Perpendicular indicators | Right-angle markers shown at each endplate midpoint |
| SRS classification | Normal / Mild / Moderate / Severe with color-coded badge |
| Draggable handles | Drag any point to refine placement — angle updates live |
| Undo / Reset | Step-by-step undo or full reset |
| Image enhancement | Brightness, contrast, and invert (negative film) sliders |
| Export PNG | Exports composite image with Cobb angle watermark |
| Zoom & pan | Scroll-wheel zoom centred on cursor · Space+drag to pan |
| Keyboard shortcuts | `Ctrl Z` undo · `F` fit · `Scroll` zoom |

---

## Measurement Method

The **classic Cobb method (1948)** is used:

1. Identify the **upper end vertebra** — the most tilted vertebra at the cephalad end of the curve.
2. Identify the **lower end vertebra** — the most tilted vertebra at the caudal end of the curve.
3. Draw a line along the **superior endplate** of the upper end vertebra.
4. Draw a line along the **inferior endplate** of the lower end vertebra.
5. The **Cobb angle** = angle between these two lines (mathematically equivalent to the angle between their perpendiculars).
6. The **apical vertebra** — the most laterally displaced and/or most rotated vertebra — is marked for reference.

**Angle calculation:**  
Direction vectors of each endplate line are normalised to the rightward direction, then:
```
Cobb angle = arccos( v1 · v2 / (|v1| × |v2|) )
```

---

## SRS Severity Classification

| Cobb Angle | Classification |
|---|---|
| < 10° | Normal |
| 10° – 24° | Mild scoliosis |
| 25° – 40° | Moderate scoliosis |
| > 40° | Severe scoliosis |

---

## Clinical References

1. **Cobb JR** (1948). Outline for the study of scoliosis. *AAOS Instructional Course Lectures*, 5:261–275. https://doi.org/10.1097/BRS.0b013e3181941755
2. **Morrissy RT et al.** (1990). Measurement of the Cobb angle on radiographs of patients who have scoliosis. *J Bone Joint Surg Am*. https://pubmed.ncbi.nlm.nih.gov/2254369/
3. **Langensiepen S et al.** (2013). Measuring procedures to determine the Cobb angle in idiopathic scoliosis. *Eur Spine J*. https://pubmed.ncbi.nlm.nih.gov/23076403/
4. **Gao et al.** (2018). Measurement of scoliosis Cobb angle by end vertebra tilt angle method. *J Orthop Surg Res*. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6124002/
5. **Scoliosis Research Society** — Classification and treatment thresholds. https://www.srs.org

---

## Deploy to GitHub Pages

```bash
# 1. Create a new repo on GitHub named "cobb-angle-app"
# 2. From the cobb-angle-app folder:
git init
git add .
git commit -m "Initial commit: CobbMeasure app"
git branch -M main
git remote add origin https://github.com/<your-username>/cobb-angle-app.git
git push -u origin main

# 3. In GitHub → Settings → Pages → Source: Deploy from branch "main" → / (root)
# 4. Your app will be live at:
#    https://<your-username>.github.io/cobb-angle-app/
```

---

## Usage

1. Open the app in any modern browser (Chrome, Firefox, Safari, Edge).
2. Load a PA/AP whole-spine radiograph (drag & drop or click the upload panel).
3. Follow the 4-step workflow in the left sidebar:
   - **Step 2:** Click two points along the superior endplate of the uppermost tilted vertebra.
   - **Step 3:** Click two points along the inferior endplate of the lowest tilted vertebra.
   - **Step 4:** Click the centre of the apical vertebra.
4. The Cobb angle is calculated and displayed instantly.
5. Drag any handle to refine placement.
6. Click **Export PNG** to save the annotated image.

> **Note:** This tool is intended for educational and research purposes. Clinical decisions should always involve a qualified spine specialist.

---

## Tech Stack

- Pure HTML / CSS / JavaScript — zero dependencies, zero build step
- Canvas API for image rendering and interactive overlay
- Single-file deployment: `index.html`
