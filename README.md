# pipeline-sensor-anomaly-detection
# 🛢️ Real-Time Pipeline Sensor Anomaly Engine

An unsupervised machine learning pipeline designed for high-frequency oil & gas sensor telemetry processing. This engine identifies operational anomalies—such as pressure drops (potential leakages) or pressure spikes (valve blockages)—before catastrophic equipment failure occurs.


## 📌 Problem Statement
Offshore and onshore pipeline networks stream thousands of telemetry events per hour (pressure PSI, flow rates BPD, and temperature). Traditional fixed-threshold alerts cause extreme "alarm fatigue" by flagging normal operational fluctuations while missing subtle, compound sensor anomalies.

This project implements a time-series feature engineering pipeline coupled with an **Isolation Forest** model to detect multivariate operational anomalies with low false-positive rates.


## 🛠️ Tech Stack & Methods
* **Language:** Python 3.10+
* **Data Processing & Feature Engineering:** `Pandas`, `NumPy`, `SciPy`
* **Machine Learning:** `Scikit-Learn` (Isolation Forest)
* **Visualization:** `Matplotlib`, `Seaborn`
* **Environment:** Google Colab


## 🔬 Methodology & Architecture

1. **Synthetic Telemetry Generation / Data Ingestion:**
   * Simulated high-frequency time-series telemetry across 1,000 temporal intervals representing pressure (PSI), flow rate (BPD), and temperature (°C).
   * Injected operational edge cases (leakage events and flow restriction blockages).

2. **Temporal Feature Engineering:**
   * **Rolling Statistics:** Calculated 12-period moving averages and rolling standard deviations to capture baseline drift.
   * **First-Order Derivatives:** Derived rate-of-change metrics ($\Delta P / \Delta t$) to detect instantaneous pressure transients.

3. **Unsupervised Anomaly Detection:**
   * Fitted an `Isolation Forest` model ($N=100$ estimators, 0.02 contamination factor) on the engineered feature space.
   * Identified anomalous timestamps based on multi-variate isolation depth scores.


## 📊 Visual Results

<img width="4200" height="2400" alt="pipeline_anomaly_detection" src="https://github.com/user-attachments/assets/ede5a5bf-24a2-4141-8023-e5f6584dd515" />

> **Key Finding:** The Isolation Forest successfully isolated 100% of injected rapid pressure drops and flow rate anomalies without triggering false alarms during baseline operational sine-wave cycles.

## 🚀 How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/ohabuenyirita/pipeline-sensor-anomaly-detection.git
