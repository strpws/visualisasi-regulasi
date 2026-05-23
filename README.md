# Perubahan Kuota Jalur Mandiri PTN

A self-contained, square (1:1) editorial infographic tracing how regulation has
progressively loosened the **jalur mandiri** admission quota at Indonesian state
universities (PTN-BH) over a decade, and flagging the less-visible structural
change in the *Daya Tampung* denominator introduced by Permen 3/2026.

Built as a single static HTML file for embedding inside a longform article. The
canvas is a perfect square that scales cleanly from **640×640px to 1080×1080px**
(social-card / Instagram dimensions).

## Preview

The graphic is a single file with no build step. Open it directly, or serve the
folder and open `http://localhost:4321`:

```bash
python -m http.server 4321
```

A ready-made launch config lives at `.claude/launch.json` (server name `static`).

## The data

Composition of admission quota at PTN-BH across four regulations. Bars show each
pathway as a percentage **of the regulated Daya Tampung**.

| Regulasi | Prestasi | Tes | Mandiri | Frekuensi mandiri |
|---|---|---|---|---|
| Permenristekdikti 126/2016 | min. 30% | min. 30% | maks. 30% | 1x per tahun |
| Permendikbudristek 48/2022 | min. 20% | min. 30% | maks. 50% | Tidak diatur; gelombang lanjutan s.d. 15 Agt |
| Permendikbudristek 62/2023 | min. 20% | min. 30% | maks. 50% | Tidak diatur; gelombang lanjutan s.d. 15 Agt |
| Permendiktisaintek 3/2026 | min. 20% | min. 30% | sisa, tanpa plafon (≤50% PTN-BH) | Tidak diatur; gelombang lanjutan s.d. 15 Agt |

**Catatan**

- Angka 2016 belum membedakan PTN-BH dan berlaku untuk semua PTN; sejak 2022
  angka khusus PTN-BH.
- Permendiktisaintek 3/2026 baru berlaku mulai tahun ajaran 2027/2028.
- Pasal 13 Permen 3/2026 mengeluarkan AMN, ADik, dan program internasional dari
  Daya Tampung. Karena denominatornya menyusut, 50% mandiri pada 2026 tidak
  setara dengan 50% pada 2022.
- Diolah: Kompas/EKI/FAI/SPW.

## How it works

- **Layout** — fixed square (`.card`) declared as a CSS container
  (`container-type: size`). Everything inside is sized in `cqmin` units, so the
  whole graphic scales proportionally with the square at any size in range.
- **Chart** — each regulation is a node on a vertical timeline; its bar is a
  100%-stacked composition (Seleksi Prestasi / Seleksi Tes / Jalur Mandiri). The
  2026 mandiri segment is hatched to mark the removal of the explicit ceiling.
- **Interaction** — segments are hoverable and keyboard-focusable; a tooltip
  shows the exact min/max wording. Frequency notes sit as a visible line under
  each bar.
- **Motion** — bars grow and rows fade in on load; respects
  `prefers-reduced-motion`.
- **Accessibility** — `role="img"` + descriptive `aria-label` on the canvas, and
  the full dataset is mirrored in a visually hidden `<table>`.

## Design system

Follows `VISUAL-GUIDELINES-basic.md` (editorial data-story system inspired by
Kompas.id longform): Lora + PT Sans, blue as the workhorse data color, gold for
the milestone/emphasis element, red reserved for narrative words only.

## Files

```
index.html                 The infographic (everything lives here)
VISUAL-GUIDELINES-basic.md  Design system reference
.claude/launch.json         Local preview server config
README.md                   This file
```

## Exporting a static image

Open at exactly 1080×1080 and screenshot the white card (no browser chrome), or
use a headless browser to capture the `.card` element.
