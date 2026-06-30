# SurveyChartStudio

SurveyChartStudio is a client-side, single-page web application designed to parse survey responses from various data formats and generate high-contrast, print-legible charts. The application is specifically engineered for black-and-white print outputs and photocopier reproduction, mitigating visual ambiguity caused by flat-color fills or overlapping labels.

## Core Features

### Multi-Format Input Parsing
The application detects file types from extension or content sniffing and implements custom client-side parsing routines for:
- Tabular data formats: CSV, TSV, JSON, and Excel (`.xlsx`, `.xls`) files.
- Google Forms summary exports: Text-based PDFs and raw copy-pasted text.
- Charts and tables: Extraction of labels and numerical values from images (PNG, JPG) using client-side Optical Character Recognition (OCR) fallback.

### Accessible Grayscale Rendering
To ensure readability when printed or photocopied in pure black-and-white, the application implements:
- **Monochrome Patterns**: Dynamic generation of eight distinct high-contrast canvas pattern fills (solid, diagonal lines, back-diagonal lines, cross-hatch, dots, dense diagonal lines, horizontal lines, and vertical lines) overlaid on colors.
- **Non-Overlapping Radial Leader Lines**: A custom Chart.js plugin that projects slice boundaries radially outward to staggered text labels, utilizing a Y-coordinate relaxation algorithm to prevent text collisions.
- **Direct Bar Annotations**: Exact values and percentages displayed adjacent to horizontal or vertical bars to negate dependencies on scale colors.

### High-DPI Exports
- Export individual charts as PNGs named following the `{question_slug}_{chart_type}.png` convention.
- Export the entire dashboard as a stacked-grid PNG layout at 2x pixel density.
- On-screen print verification via a grayscale simulation toggle.

## Technical Architecture

The application is built using a serverless, client-side architecture requiring no backend database or network dependencies.
- **Rendering Framework**: Chart.js (v4.4.1) UMD
- **CSV Parsing**: PapaParse (v5.4.1)
- **Spreadsheet Parsing**: SheetJS (v0.18.5)
- **PDF Scraping**: PDF.js (v3.11.174)
- **In-Browser OCR**: Tesseract.js (v5.0.0)
- **DPI Scaling**: html2canvas (v1.4.1)

## Setup and Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/sheikhsajid69/graphs-from-google-form-responses.git
   ```
2. Open `index.html` in any modern web browser.
3. No build steps, installations, or local server instances are required for basic usage.

## License

This project is licensed under the Apache License 2.0. Refer to the LICENSE file for details.
