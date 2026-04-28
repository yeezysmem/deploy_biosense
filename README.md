# BioSense360 — Thermal Comfort Dashboard

> Real-time monitoring of thermal comfort using the Humidex index  
> M1 Artificial Intelligence Project — University of Toulouse · Client: **Neusta**

---

## Overview

**BioSense360** is an interactive thermal monitoring dashboard designed to assess heat-related risks in the workplace. It combines outdoor weather data (Météo France — Toulouse-Blagnac station) with indoor sensor data (Neusta ClimaTrack MKII) to produce hourly Humidex classifications and safety recommendations aligned with current regulatory standards.

The underlying classification model is a **Random Forest** (500 trees, entropy criterion), achieving **99.98% accuracy** on test data and **99.05%** on Neusta validation data.

---

## Features

### Daily Analysis
- Annual thermal calendar (8 Humidex levels)
- Data source selection (outdoor / indoor)
- Daily statistics (max class, temperature, humidity)
- Hourly charts (Humidex + temperature)
- Class distribution (donut chart)
- Dynamic safety recommendations
- Detailed hourly table
- Timeline visualization

### Map & Mobility
- Interactive heat map (Leaflet)
- Station-based visualization
- Thermal mobility recommendation engine:
  - Departure / destination selection
  - 8×8 risk matrix
  - 4-step protocol (Before · Transit · Arrival · Monitoring)
  - Acclimatization estimation
  - Automatic legal alerts

---

## Project Structure

dashboard/
├── dashboard.html
├── dashboard_data.js
└── prepare_dashboard_data.py

---

## Setup

### Requirements
- Python 3.9+
- Modern browser (Chrome, Firefox, Edge)
- Internet connection (for CDN libraries)

### 1. Prepare data

python prepare_dashboard_data.py

### 2. Run dashboard

# from dashboard folder
open dashboard.html          # macOS
xdg-open dashboard.html      # Linux
start dashboard.html         # Windows

> Make sure `dashboard_data.js` is in the same folder as `dashboard.html`.

---

## Humidex Model

e = 6.112 × 10^(7.5T / (237.7 + T)) × RH / 100  
HX = T + 0.5555 × (e − 10)

Where:
- T = temperature (°C)  
- RH = relative humidity (%)  

---

## Classification Scale

| Class | Humidex | Level |
|------|--------|------|
| 0 | < 25 | Normal |
| 1 | 25–30 | Mild discomfort |
| 2 | 30–34 | Caution |
| 3 | 34–38 | Discomfort |
| 4 | 38–40 | Alert |
| 5 | 40–43 | Intense discomfort |
| 6 | 43–45 | Danger |
| 7 | ≥ 45 | Extreme danger |

---

## Tech Stack

- Frontend: HTML, CSS, JavaScript
- Visualization: Chart.js
- Mapping: Leaflet
- Data Processing: Python
- ML Model: Random Forest (scikit-learn)

---

## References

- OHCOW (2022)
- ACGIH TLV (2023)
- NIOSH (2016)
- HAS (2023)
- INRS R-447
- Masterton & Richardson (1979)

---

## Team

- Daniil Zhdanov  
- Nourhane Mallek  
- Soufiane Khallouki  

---

## Notes

This project was developed as part of the M1 Artificial Intelligence program at the University of Toulouse in collaboration with **Neusta**.
