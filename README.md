# ⚡ GridAlpha: Modeling and Valuation of UK Battery Energy Storage Systems

This repository contains a research-driven project exploring the **technical optimization** and **commercial valuation** of grid-scale Battery Energy Storage Systems (BESS) in the UK electricity market.  

The project is divided into two integrated components:  

1. **A trading optimization model** that simulates the daily operation of a BESS across multiple UK electricity markets.  
2. **An investment analysis framework** that uses model outputs to evaluate the financial impact of emerging battery technologies.  

---

## 📌 Project Objectives  

1. **Develop a digital twin of a BESS asset** that optimally allocates capacity across wholesale arbitrage, ancillary services, and the Balancing Mechanism.  
2. **Quantify the impact of technical parameters** such as round-trip efficiency, degradation costs, and storage duration on asset profitability.  
3. **Evaluate new technologies and business models** by translating operational improvements into lifetime Net Present Value (NPV) uplifts.  
4. **Produce an investment case study** for a hypothetical UK-based battery technology company, using the optimization model as quantitative evidence.  

---

## 🔹 Technical Scope  

### Battery Physics & Constraints  
- Rated Power (MW) and Energy Capacity (MWh)  
- Round-trip efficiency and charge/discharge limits  
- State of Charge (SoC) tracking across time steps  
- Degradation cost per MWh cycled, derived from capex and cycle life assumptions  

### Market Participation  
The model considers the principal revenue streams available to UK BESS assets:  

- **Wholesale Arbitrage**: Charging in low-price periods and discharging in high-price periods, using half-hourly system prices from Elexon BMRS.  
- **Ancillary Services (Dynamic Containment, etc.)**: Committing capacity for frequency response with guaranteed returns, balanced against lost arbitrage opportunities.  
- **Balancing Mechanism (BM)**: Modeling short-notice system actions using historical imbalance and acceptance price data.  
- **Capacity Market (CM)**: Annual fixed revenue stream for availability, treated as a baseline contribution to profitability.  

### Optimization Engine  
- Formulated as a **linear optimization problem**, solved with `pulp` or `pyomo`.  
- Objective function maximizes daily net profit, accounting for:  
  - Market revenues  
  - Opportunity costs  
  - Degradation costs  
- Modular design allows comparison of single-market vs. multi-market strategies.  

---

## 🔹 Commercial Scope  

### Investment Analysis Framework  
The trading model forms the quantitative foundation of a broader commercial study.  

1. **Baseline Case**: Profitability of a standard 1-hour / 2-hour BESS asset with conventional performance assumptions.  
2. **Technology Case**: Adjusted parameters to reflect innovations such as:  
   - Higher round-trip efficiency  
   - Extended cycle life  
   - AI-driven battery management software  
3. **Valuation Impact**:  
   - Daily profit uplift scaled to annual returns  
   - Lifetime NPV with and without technology  
   - Sensitivity analysis on degradation cost, volatility, and contract prices  

### Case Study: Hypothetical UK Startup  
The investment framework is applied to a fictional battery technology company, modeled as if under due diligence by a climate-tech investor.  
- **Product**: AI-powered battery management system reducing degradation by ~30%.  
- **Market Context**: UK grid-scale BESS pipeline projected to grow >25% CAGR.  
- **Quantified Advantage**: Increased asset lifetime value demonstrated through model outputs.  

---

## 🗂 Repository Structure  

```bash
gridalpha-bess-valuation/
│
├── data/                # Raw and processed datasets (BMRS, ESO, CM)
│   ├── raw/             # Direct downloads (CSV/JSON/XML from APIs)
│   └── cleaned/         # Standardized, timezone-aligned, validated
│
├── notebooks/           # Jupyter notebooks for exploratory analysis
│   ├── data_cleaning.ipynb
│   ├── arbitrage_model.ipynb
│   ├── ancillary_services.ipynb
│   └── investment_case.ipynb
│
├── src/                 # Core modules
│   ├── battery/         # Physics & degradation model
│   ├── markets/         # Arbitrage, services, BM, CM modules
│   ├── optimizer/       # Dispatch optimization engine
│   └── utils/           # Shared helpers (timezones, data validation)
│
├── dashboard/           # Streamlit app for visualization
│   ├── app.py
│   └── components/      
│
├── reports/             # Written outputs
│   ├── investment_memo_draft.docx
│   ├── figures/         # Charts generated from model
│   └── final_memo.pdf
│
├── tests/               # Unit and integration tests
│
└── README.md            # Project documentation
