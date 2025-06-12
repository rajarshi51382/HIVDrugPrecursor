# HIVDrugPrecursor
This project explores the use of machine learning to assist in early-stage drug discovery for HIV. By leveraging molecular data and predictive modeling, it aims to provide a cost-effective, data-driven method to identify chemical compounds that may inhibit critical HIV-related proteins.

## Overview

This project explores the use of machine learning to assist in early-stage drug discovery for HIV. By leveraging molecular data and predictive modeling, it aims to provide a cost-effective, data-driven method to identify chemical compounds that may inhibit critical HIV-related proteins.

## Motivation

- HIV (Human Immunodeficiency Virus) attacks the immune system, leaving patients vulnerable to infections.
- Over 39.9 million people worldwide are living with HIV, with more than 2.1 million deaths annually.
- There is currently no cure or vaccine, and treatments are often expensive.
- Machine learning can support researchers in filtering potential drug candidates more efficiently.

## Objectives

- Identify chemical compounds that inhibit key proteins involved in HIV replication and proliferation.
- Use molecular descriptors and classification techniques to predict compound efficacy.
- Evaluate drug-likeness using Lipinski’s Rule of Five.
- Build a reproducible pipeline for bioactivity prediction using open data.

## Target Proteins

The project targets three HIV-related proteins:

- **HIV Protease** – Facilitates replication of the virus.
- **CCR5** – A receptor that allows HIV to enter human cells.
- **KAT5 (Tip60)** – Influences transcriptional regulation and proliferation of the virus.

## Methodology

### 1. Data Collection
- Sourced from the **ChEMBL** database.
- Compounds retrieved based on reported inhibition activity against the target proteins.
- Activity levels categorized into:
  - **Active**: Strong inhibition
  - **Moderate**: Partial inhibition
  - **Inactive**: Little to no inhibition

### 2. Drug-likeness Filtering
Applied **Lipinski’s Rule of Five** to assess oral bioavailability:
- Molecular weight ≤ 500
- LogP ≤ 5
- Hydrogen bond donors ≤ 5
- Hydrogen bond acceptors ≤ 10
- Molecular refractivity between 40–130

### 3. Feature Engineering
- Molecular structures encoded using **Morgan Fingerprints** (a form of circular fingerprinting).
- Fingerprints represent molecules numerically for input into ML models.

### 4. Modeling
- Regression models trained to predict inhibition activity.
- Used `LazyPredict` to benchmark multiple models.
- Selected **RandomForestRegressor** for final evaluation.

### 5. Evaluation
Performance was measured using the R² (coefficient of determination):

| Protein      | R² Score |
|--------------|----------|
| KAT5         | 0.6368   |
| CCR5         | 0.5068   |
| HIV Protease | 0.3965   |

## Limitations and Future Work

- Models trained on limited 2D descriptors; integration of 3D structure data could improve accuracy.
- Further hyperparameter tuning and custom model architecture design are likely to improve results.
- Potential to expand this pipeline to multi-target inhibitors and other viral diseases.

## References

- ChEMBL database: https://www.ebi.ac.uk/chembl/
- Bioactivity threshold guidance: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3168031/
- KAT5: https://en.wikipedia.org/wiki/KAT5  
- CCR5: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3185609/  
- HIV Protease: https://pubmed.ncbi.nlm.nih.gov/3290901/
