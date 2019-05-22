# CAMDA Challenge: Predict drug toxicity
An ensemble learning approach for modeling the systems biology of drug-induced injury in human liver

## Getting Started

These instructions will guide you through the code used to participate at the CAMDA CMap drug safety challenge. All the scripts are written in R and most of them are R Markdowns that improve the readability of the code.

### Prerequisites

What packages you need to install. Some instructions are given at the R Markdowns.

```
cmapR
ComplexHeatmap
caret
```

### Outline

1. Analyze the compounds
2. Identify gene signature to separate DILI and no-DILI drugs
3. Classify drugs using different features

### 1. Analyze the compounds

Script: `analysis_of_compounds.Rmd`.
We first analyzed the different DILIRank categories for each compound, removing the ambiguous drugs. Then, we analyzed the number of gene expression samples for each compound depending on the conditions of cell line, concentration and time. We written a summary of the analysis in the table `summary_compounds.tsv`.

### 2. Identify gene signature to separate DILI and no-DILI drugs

Script: `gene_test_across_samples_phh_10_24_mixlessmost.Rmd`.
First, we retrieved the gene expression samples from cell line PHH (liver primary cell), dose concentration 10 µM and time 24 h. 
Then, for each landmark gene, we calculated a Wilcoxon test between the gene expression values of the DILI and no-DILI drugs. We written a summary of the output values in the table `gene_test_landmark_phh_10_24_noout_mixlessmost.tsv` and a heatmap in `heatmap_phh_mixlessmost_10_24_landmark_noout_above1_5_mixlessmost.pdf`.

### 3. Classify drugs using different features

We used different scripts to classify the drugs depending on the feature:

* **Gene signature**: `classify_drugs_mixlessmost_wilcox.Rmd`
* **Hub genes**: `classify_drugs_mixlessmost_hub.Rmd`
* **DisGeNET genes**: `classify_drugs_mixlessmost_disgenet.Rmd`
* **SMILES**: `classify_drugs_mixlessmost_smiles.Rmd`
* **Drug targets**: `classify_drugs_mixlessmost_targets.Rmd`
* **Combining gene signature & SMILES**: `classify_drugs_mixlessmost_combined_wilcoxsmiles.Rmd`
* **Combining gene signature & drug targets**: `classify_drugs_mixlessmost_combined_wilcoxtargets.Rmd`
* **Combining gene signature & SMILES & drug targets**: `classify_drugs_mixlessmost_allcombined.Rmd`

To create the SMILES data, we used the script `calculate_smiles.R`.
To validate the predictions, we used the script `validate_drugs.Rmd`.
The validations are in the folder `outputs/validations`.