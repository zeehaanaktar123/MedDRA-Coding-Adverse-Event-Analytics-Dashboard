# MedDRA Case Analytics & Signal Detection Dashboard

An interactive **Power BI** dashboard for pharmacovigilance case analytics — combining MedDRA hierarchy exploration, PRR/ROR-based signal detection, and case demographics/outcomes analysis across 900 mock spontaneous adverse event reports.

> ⚠️ **Disclaimer:** All drug names, events, and case data are entirely fictional, generated for demonstration purposes only.

## 📊 Project Overview

Drug safety teams need to move fluidly between three views of the same case data: a high-level executive summary, a structured MedDRA coding hierarchy, and a statistical signal detection matrix — all cross-filterable by drug, country, and event. This project builds that workflow end-to-end across **900 case reports**, **7 countries**, **6 fictional drugs**, and the full **SOC → HLGT → LLT** MedDRA hierarchy, to answer:

- How many cases are serious or fatal, and how has reporting volume trended by quarter?
- Which System Organ Classes (SOCs) and specific reaction terms carry the most cases and the highest seriousness rate?
- Which drug-event combinations show statistical disproportionality (PRR/ROR) that would flag them as potential safety signals?
- What do the underlying patient demographics, causality assessments, and case outcomes look like?

<img width="1433" height="806" alt="Screenshot 2026-09-02 030655" src="https://github.com/user-attachments/assets/a4cc2a81-a1be-4e74-920c-0b1aa5fd57f0" />
<img width="1438" height="806" alt="Screenshot 2026-09-02 030744" src="https://github.com/user-attachments/assets/9dff0aee-ae18-44a6-92e6-a333ef05d5c8" />
<img width="1437" height="805" alt="Screenshot 2026-09-02 030820" src="https://github.com/user-attachments/assets/7d630623-5719-4b90-8bfd-c12325f5dc8f" />
<img width="1435" height="806" alt="Screenshot 2026-09-02 030902" src="https://github.com/user-attachments/assets/756ac036-4859-45ad-be1a-34710881e312" />


## 🛠️ What I Did

- Modeled a 900-row case-level dataset (drug, MedDRA SOC/HLGT/LLT, seriousness, outcome, causality assessment, age group, country, report date) in Power BI.
- Built DAX measures for **Total Cases, Serious Cases, % Serious, Fatal Cases**, and per-drug/per-event **PRR, ROR, and Signal Flag** calculations.
- Designed a 4-page interactive report with a consistent branded navigation bar and full cross-page filtering:
  - **Executive Overview** — headline KPIs (Total, Serious, % Serious, Fatal Cases), a horizontal bar chart of cases by System Organ Class, and a quarterly case-volume trend line.
  - **MedDRA Hierarchy Drill-Down** — a full decomposition tree letting users drill from Total Cases through **HLGT → LLT → Drug Name**, paired with a treemap and a detail table of cases and % serious by SOC.
  - **Signal Detection** — a PRR/ROR disproportionality matrix (Preferred Term × Drug) with conditional-formatted signal flags, plus country-filter buttons (Australia, Canada, France, Germany, India, UK, USA) for regional signal review.
  - **Demographics & Outcomes** — donut charts of cases by age group and case outcome, a horizontal bar chart of cases by WHO-UMC causality category, and a bar chart of cases by time-to-onset group.
- Implemented cross-filtering country buttons and slicers so any page's signal or hierarchy view can be sliced by geography.
- Applied conditional formatting to instantly highlight statistically flagged "SIGNAL" cells in the PRR/ROR matrix against the "No signal" background.

## 🔑 Key Outcomes & Insights

- Across **900 total cases**, **163 (18.11%) were serious**, including **18 fatal cases**.
- **Nervous system disorders** is the leading SOC by volume (238 cases), followed by **Gastrointestinal disorders** (130) and **General disorders and administration site conditions** (118) — but volume and severity don't align: **Cardiac disorders** carries the highest seriousness rate at **53.33%**, and **Musculoskeletal and connective tissue disorders** at **31.37%**, despite much lower case counts.
- Quarterly case volume held steady through Q1–Q3 (~227–232 cases) before a sharp drop in **Q4 (210 cases)**, worth investigating for reporting lag or seasonal effects.
- The PRR/ROR **Signal Detection matrix flagged 4 drug-event pairs** as statistical signals:
  - **Vertaphen–Rhabdomyolysis**: PRR 10.15, ROR 12.58 — the strongest signal in the dataset, consistent with a statin-class effect.
  - **Riboxetine–QT prolongation**: PRR 4.61, ROR 5.82.
  - **Riboxetine–Vomiting**: PRR 2.06, ROR 2.09.
  - **Riboxetine & Zolpiflex–Hepatic enzyme increased**: both PRR 2.62, ROR 2.68.
  - All other drug-PT combinations across the 6-drug × 15-PT matrix remained below the signal threshold, correctly separating true elevated pairs from background noise.
- On the **Demographics & Outcomes** page: over half of all cases (**51.89%**) had **fully recovered/resolved**, while **9.56% remained unresolved** and **2% were fatal**. Causality was most often assessed as **"Possible"** (the largest WHO-UMC category), and the majority of events had an onset of **8–30 days** after treatment start — pointing to a delayed-onset pattern worth flagging for medical review.
- Age distribution was fairly even across all five age bands (19–23% each), showing no single age group dominating the case load.

## 🧰 Tools & Skills Used

`Power BI Desktop` · `DAX` · `Data Modeling` · `Decomposition Tree` · `MedDRA Hierarchy Analysis (SOC/HLGT/LLT)` · `Disproportionality Analysis (PRR/ROR)` · `Signal Detection` · `Conditional Formatting` · `Data Visualization` · `Pharmacovigilance Analytics`


## 📁 Repository Contents

```
├── MedDRA_Project.pbix   # Power BI report file
├── screenshots/           # Dashboard screenshots
└── README.md
```

## 🚀 How to View

1. Download `MedDRA_Project.pbix`.
2. Open it in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).
3. Use the page navigation, country filter buttons, and MedDRA hierarchy slicers to explore the data interactively.
