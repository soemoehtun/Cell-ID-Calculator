# Cell ID Calculator

A lightweight, browser-based tool for encoding and decoding mobile network cell identifiers across **2G**, **3G**, **4G LTE**, and **5G NR** technologies.

---

## Overview

The Cell ID Calculator helps telecom engineers, network planners, and developers quickly convert between raw cell identifier components and their standard formatted strings — no installation, no dependencies, just open and use.

---

## Features

- **Three calculation modes** — CGI (2G/3G), ECGI (4G LTE), and NCI (5G NR)
- **Encode & Decode** — convert components → identifier string, or parse a string → components
- **Multiple output formats** — Decimal, Hexadecimal, and Binary representations
- **Formula reference** — built-in structure and formula guide for each identifier type
- **Operation Guide** — expandable guide with examples for each tab
- **Responsive design** — works on desktop, tablet, and mobile
- **No internet required** — fully self-contained HTML file

---

## How to Use

1. Open `cellid_calculator.html` in any modern web browser
2. Select the tab for your network type: **CGI**, **ECGI**, or **NCI**
3. Choose **Encode** or **Decode** mode
4. Enter the required values
5. Click **Calculate**

---

## Tabs & Identifier Types

### CGI — Cell Global Identifier (2G / 3G)

Used in GSM and UMTS networks to uniquely identify a cell worldwide.

| Field | Description |
|-------|-------------|
| MCC | Mobile Country Code — 3 digits (0–999) |
| MNC | Mobile Network Code — 2 or 3 digits (0–999) |
| LAC | Location Area Code — 16 bits (0–65,535) |
| CI | Cell Identity — 16 bits (0–65,535) |

**Format:** `MCC-MNC-LAC-CI`
**Example:** MCC=001, MNC=01, LAC=100, CI=5 → `001-01-100-5`

---

### ECGI — E-UTRAN Cell Global Identifier (4G LTE)

Used in LTE networks to globally identify a cell using the ECI (E-UTRAN Cell Identifier).

| Field | Description |
|-------|-------------|
| MCC | Mobile Country Code — 3 digits (0–999) |
| MNC | Mobile Network Code — 2 or 3 digits (0–999) |
| eNodeB ID | 20 bits (0–1,048,575) |
| Cell ID | 8 bits (0–255) |
| ECI | 28 bits (0–268,435,455) |

**Formula:** `ECI = (eNodeB_ID × 256) + Cell_ID`
**Example:** eNodeB=12345, Cell ID=2 → ECI = `3,160,322`

---

### NCI — NR Cell Identifier (5G NR)

Used in 5G NR networks within the NCGI (NR Cell Global Identifier). The 36-bit NCI is split between gNodeB ID and Cell ID with configurable bit widths.

| Field | Description |
|-------|-------------|
| MCC | Mobile Country Code — 3 digits (0–999) |
| MNC | Mobile Network Code — 2 or 3 digits (0–999) |
| gNodeB ID | 22–32 bits (configurable by operator) |
| Cell ID | 4–14 bits (= 36 − gNodeB bits) |

**Formula:** `NCI = gNodeB_ID × 2^(Cell_ID_bits) + Cell_ID`
**Default (22/14 split):** `NCI = gNodeB_ID × 16384 + Cell_ID`
**Example:** gNodeB=100, Cell ID=1 → NCI = `1,638,401`

---

## Encode Mode

Enter individual components (MCC, MNC, etc.) and the tool will:
- Generate the full identifier string
- Show all output representations (Decimal, Hex, Binary)

## Decode Mode

Enter a full identifier value and the tool will:
- Break it down into its component parts
- Display each component in multiple formats

---

## File Structure

```
Frequency Calculator/
│
├── cellid_calculator.html     # Main tool (single self-contained file)
└── README.md                  # This file
```

---

## Browser Support

| Browser | Supported |
|---------|-----------|
| Chrome | ✅ |
| Firefox | ✅ |
| Safari | ✅ |
| Edge | ✅ |

---

## Technical Notes

- Pure **HTML + CSS + JavaScript** — no frameworks or libraries
- Font: **Helvetica Neue / Helvetica**
- Fully **offline capable** — no external requests after initial load
- Responsive layout with breakpoints at **1024px**, **860px**, **600px**, and **400px**

---

## Standards Reference

| Identifier | Standard |
|------------|----------|
| CGI | 3GPP TS 23.003 |
| ECGI | 3GPP TS 36.413 |
| NCI / NCGI | 3GPP TS 38.413 |

---

## License

This tool is for internal/personal use. Feel free to modify and redistribute freely.
