**This repository is under construction and will contain all code files for my Master's research project. For now, it only contains one of the simulated examples.**

# Modularised Bayesian Calibration with Gaussian Process Emulator

This repository contains a modular implementation of a **Bayesian calibration framework** using a **Gaussian Process (GP) emulator** and **Markov Chain Monte Carlo (MCMC)** sampling.  
The goal is to calibrate uncertain model parameters against observed data while efficiently emulating complex computer model outputs.

---

## Overview

This repository contains implementation a **modular GP–MCMC calibration pipeline**, structured to separate the key components of calibration.
We have also worked on a **full GP–MCMC calibration pipeline** which was computationally expensive (code available).

1. **Data Preprocessing** — Standardizes and scales the inputs/outputs for the GP emulator.  
2. **GP Emulator Construction** — Builds a Gaussian Process model of the simulator response.  
3. **Calibration via MCMC** — Samples from the posterior distribution of model parameters given data.  
4. **Posterior Analysis & Prediction** — Uses posterior draws to generate calibrated model predictions and uncertainty estimates.

The modular structure makes it easy to replace, extend, or independently test each step of the calibration workflow.

---

## Theoretical Background

The Bayesian calibration approach follows the standard model:

$$
y = \eta(x, \theta) + \delta(x) + \epsilon
$$

where:
-  $y$ = observed data  
- $\eta(x, \theta)$ = computer model output (emulated via a GP)  
- $\delta(x)$ = model discrepancy term  
- $\epsilon$ = error term  

Through calibration we want to infer the posterior distribution and uncertainty of the unknown parameters $\theta$ using Metropolis Hastings MCMC sampling.

---

## Notebook Contents

**File:** `Modularised_Calibration_Case3.ipynb`

| Section | Description |
|----------|--------------|
| **1. Imports & Setup** | Loads all required Python libraries and defines helper functions. |
| **2. Data Preprocessing** | Performs input normalization (min–max) and output standardization (mean–std). |
| **3. GP Emulator Construction** | Trains the Gaussian Process on simulator data using a custom covariance structure (`cov_eta`). |
| **4. MCMC Sampling** | Implements Bayesian inference to obtain posterior samples of calibration parameters. |
| **5. Posterior Prediction** | Uses MCMC samples to produce calibrated predictions and uncertainty intervals. |
| **6. Diagnostics & Visualization** | Generates trace plots, posterior histograms, and predictive validation plots. |

---

## Requirements

This notebook is written in **Python 3.10+** and requires the following libraries:

```bash
numpy
scipy
matplotlib
pandas
tqdm
seaborn
scikit-learn


