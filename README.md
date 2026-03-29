# VieTOUR Converter

A browser-based helper tool for converting MEWS reservation exports into the CSV format required for VieTOUR statistical reporting.

Built for **Pension Mozart, Vienna**.

---

## Overview

This tool processes reservation exports from **MEWS** and generates a CSV in the following format:

```text
Code;Land;SummeAnkuenfte;SummeNaechtigungen
```

It supports:

- German and English MEWS exports
- automatic country detection from address and/or nationality
- exclusion of cancelled reservations
- Germany and Austria mapping by federal state / Bundesland
- manual correction of unresolved records
- local override storage in the browser
- export and import of mapping overrides

The application runs entirely in the browser as a single HTML file.

---

## Features

### Multi-step workflow
The UI guides users through 4 steps:

1. **File & settings**
2. **Review results**
3. **Manual assignment**
4. **Download**

This makes the process easier to understand, especially for non-technical users.

---

### Automatic processing
The converter automatically:

- reads `.xlsx`, `.xls`, and `.csv` files
- detects supported MEWS column names
- calculates arrivals and nights for the selected reporting month
- excludes cancelled / no-show / option rows
- maps Germany by postal code to Bundesland codes
- maps Austria by postal code to Bundesland codes

---

### Manual assignment
If automatic country mapping is not possible, unresolved records can be assigned manually.

Manual assignment supports:

- regular VieTOUR destination codes
- row-specific overrides
- country-wide overrides
- postal-code-based overrides for Germany and Austria

Special fallback targets are also supported:

- `4001` – Ungeklärt
- `4002` – Unbekannt
- `4003` – International
- `4004` – Konventionsflüchtling
- `4005` – Staatenlos

Aggregate / group codes are also available:

- `4000` – Übriges Ausland
- `3700` – Zentral- und Südamerika
- `5700` – Übriges Afrika
- `5800` – Übriges Asien
- `8700` – GUS

---

### Local persistence
The tool stores some information in the browser:

- mapping overrides
- last selected reporting month
- selected country source mode

No server-side backend is required.

---

## Supported input

The tool expects a MEWS reservation export containing columns such as:

- reservation number
- first name / last name
- address
- nationality
- status / cancelled
- arrival
- departure
- person count

Both German and English header names are supported.

---

## Output

Generated output is a CSV with this structure:

```text
Code;Land;SummeAnkuenfte;SummeNaechtigungen
```

Example:

```text
Code;Land;SummeAnkuenfte;SummeNaechtigungen
1600;United Kingdom;12;36
3900;United States of America;4;10
5300;Berlin (Deutschland);2;6
```

---

## How to use

### Option 1: Run locally
1. Download or clone this repository
2. Open `index.html` in your browser
3. Upload a MEWS export
4. Select the reporting month
5. Review the generated CSV
6. Resolve open mappings if needed
7. Download the final CSV

---

### Option 2: Publish with GitHub Pages
If `index.html` is stored in the repository root, the tool can be published as a static site via GitHub Pages.

---

## Tech stack

- HTML
- CSS
- JavaScript
- [Bootstrap 5](https://getbootstrap.com/) (MIT License)
- [SheetJS / xlsx Community Edition](https://github.com/SheetJS/sheetjs) (Apache License 2.0)

---

## License

The application code in this repository is intended to be licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

Please ensure that a proper `LICENSE` file is included in the repository.

License text:
[https://www.gnu.org/licenses/agpl-3.0.html](https://www.gnu.org/licenses/agpl-3.0.html)

---

## Notes on AGPL

If this software is made available to users over a network, AGPL obligations may apply, including providing access to the corresponding source code.

This repository should therefore include:

- `LICENSE`
- this `README.md`
- the application source (`index.html`)

---

## Project background

Originally created for:

**Pension Mozart, Vienna**  
https://www.pension-mozart.at

Developed by:

**SORWELL Media & Events e.U.**  
https://www.sorwell.eu

---

## Disclaimer

This tool is provided as-is, without warranty of any kind.  
Please verify generated results before submitting official statistics.
