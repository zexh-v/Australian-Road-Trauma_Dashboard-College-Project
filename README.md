# Australian Road Trauma Dashboard

An interactive data visualisation dashboard for **COS30045 Data Visualisation** (Group 23), built to make it easier to explore Australian road crash hospitalisation data published by the Bureau of Infrastructure and Transport Research Economics (BITRE), based on AIHW records covering **2011–2021**.

Road crash data from AIHW is normally published as large Excel tables that are difficult to compare across time periods, road user types, or states. This dashboard pulls the key figures into an interactive interface so that hospital managers, healthcare planners, road safety researchers, and policymakers can quickly see trends and comparisons without manually working through spreadsheets.

## What the Dashboard Shows

The dashboard is split into three views:

- **National Overview** — how traffic injury hospitalisations and acute bed days changed across Australia year by year, and which road user types (car occupants, motorcyclists, cyclists, pedestrians, etc.) account for the most admissions and bed days.
- **First Nations** — a comparison of admission trends and inpatient days between First Nations and non-Indigenous people, broken down by road user type.
- **State & Territory** — hospitalisations and bed days across Australia's eight states and territories, with a road-user heatmap to show each jurisdiction's mix of road user types.

Users can filter by year, by state/territory, and by road user type. All charts update immediately when a filter changes.

## Data

Three CSV files (processed from BITRE Excel workbooks using KNIME) are loaded at runtime:

| File | Rows | Covers |
|---|---|---|
| `data/Hospitalisation.csv` | 1,584 | National, all transport causes |
| `data/state_road_user.csv` | 1,210 | Per state/territory, by road user |
| `data/first_nations_road_user.csv` | 307 | First Nations vs. Non-Indigenous, by road user |

The key measures are **hospitalisations** (`hosp`) and **bed days excluding patients who died** (`bed_days_excl_died`). Average length of stay is derived by dividing bed days by admissions. Counts are not adjusted for population size.

## Running Locally

The dashboard loads CSV files at runtime, so it must be served over HTTP — opening `index.html` directly as a `file://` URL will not work.

**VS Code Live Server** (recommended): open the `Website_3` folder and click *Go Live*.

**Python:**
```bash
cd Website_3
python -m http.server 8080
```
Then open `http://localhost:8080`.

## Built With

- [D3.js](https://d3js.org/) v7.9.0 — all chart rendering and data aggregation
- Vanilla HTML, CSS, and JavaScript — no build tools or frameworks required

## Generative AI Disclosure

OpenAI ChatGPT / Codex and Gemini Antigravity assisted with HTML/CSS layout, JavaScript troubleshooting, and D3 chart code. A summary of the prompts used is in the comments at the top of `index.html`.