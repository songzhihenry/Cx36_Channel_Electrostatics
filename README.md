# Electrostatic Interaction Determines the Docking Specificity and the Formation of Functional Cx36 Gap Junction Channels

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## Abstract

Connexin36 (Cx36) is broadly expressed in neurons and serves as the principal protein to form interneuronal gap junctions (GJs), also known as electrical synapses. Recent high-resolution structures of human Cx36 GJ have revealed crucial electrostatic interactions (ESIs) between two docked Cx36 hemichannels at the second extracellular (E2) loops. Despite their structural importance, the functional roles of these ESIs remain poorly understood. 

To investigate their significance, we systematically designed and tested a series of missense variants targeting key E2 interface residues, aiming to disrupt or modulate the electrostatic landscape at the docking interface. Based on the ESI pairs defined from the crystal structure, our combined computational calculations and dual patch-clamp experiments in engineered HEK293 cell pairs suggest that at least three ESI residual pairs per E2-E2 interface are required to support functional GJ formation. 

Furthermore, we found that these unique ESIs of Cx36 ensure its docking specificity to itself, preventing the formation of heterotypic GJs with other brain connexins (Cx26, Cx30, Cx31.3, Cx32, Cx43, Cx45, Cx47). Overall, these findings provide essential molecular and functional insights into the mechanisms governing Cx36 GJ formation and partner specificity, paving the way for future therapeutic approaches targeting connexin dysfunction in human diseases.

---

## Repository Contents

This repository contains the source data and analysis code supporting the manuscript. The data includes computational energy calculations for various Cx36 mutants analyzed using FoldX, along with correlation analysis between electrostatic interactions and functional outcomes.

### File Structure

```
Cx36_Channel_Electrostatics/
│
├── README.md                    # This file
├── cx36_mut_corr.ipynb         # Main Jupyter notebook for data analysis
├── 8iyg_all.csv                # Combined data for 8iyg structure
├── 8xgd_all.csv                # Combined data for 8xgd structure
│
├── 8iyg_hetero/                # Heterotypic mutant data for 8iyg structure
│   ├── Average_8iyg.fxout
│   ├── Average_8iyg_e241k.fxout
│   ├── Dif_8iyg.fxout
│   ├── Dif_8iyg_e241k.fxout
│   ├── Raw_8iyg.fxout
│   ├── Raw_8iyg_e241k.fxout
│   └── PdbList_8iyg.fxout
│
├── 8iyg_homo/                  # Homotypic mutant data for 8iyg structure
│   ├── Average_8iyg.fxout
│   ├── Average_8iyg_e241k.fxout
│   ├── Dif_8iyg.fxout
│   ├── Dif_8iyg_e241k.fxout
│   ├── Raw_8iyg.fxout
│   ├── Raw_8iyg_e241k.fxout
│   └── PdbList_8iyg.fxout
│
├── 8xgd_hetero/                # Heterotypic mutant data for 8xgd structure
│   └── [Similar structure as 8iyg_hetero]
│
└── 8xgd_homo/                  # Homotypic mutant data for 8xgd structure
    └── [Similar structure as 8iyg_homo]
```

### Data Description

- **FoldX Output Files (.fxout)**: Computational energy calculations from FoldX for different mutant configurations
  - `Average_*.fxout`: Averaged energy values across multiple models
  - `Dif_*.fxout`: Difference in energy compared to wild-type
  - `Raw_*.fxout`: Raw energy calculations
  - `PdbList_*.fxout`: List of PDB structures used in calculations

- **Structure Labels**:
  - `8iyg`: Human Cx36 gap junction structure (PDB: 8IYG)
  - `8xgd`: Alternative Cx36 structure (PDB: 8XGD)

- **Mutant Types**:
  - `hetero`: Heterotypic configurations (different mutations on opposing hemichannels)
  - `homo`: Homotypic configurations (same mutations on both hemichannels)

---

## Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Required Python Packages

Install all required packages using pip:

```bash
pip install pandas matplotlib seaborn numpy scipy scikit-learn
```

Or install from requirements file (if provided):

```bash
pip install -r requirements.txt
```

### Detailed Package List

The analysis notebook uses the following Python packages:

- **pandas** (≥1.3.0): Data manipulation and analysis
- **matplotlib** (≥3.4.0): Data visualization and plotting
- **seaborn** (≥0.11.0): Statistical data visualization
- **numpy** (≥1.21.0): Numerical computing
- **scipy** (≥1.7.0): Scientific computing and statistical tests
- **scikit-learn** (≥0.24.0): Machine learning tools (silhouette score, clustering metrics)

### Verification

To verify your installation, open Python and run:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
from scipy.stats import linregress, mannwhitneyu
from sklearn.metrics import silhouette_score

print("All packages imported successfully!")
```

---

## Usage

### Running the Analysis

1. **Clone the repository:**
   ```bash
   git clone https://github.com/songzhihenry/Cx36_Channel_Electrostatics.git
   cd Cx36_Channel_Electrostatics
   ```

2. **Install dependencies:**
   ```bash
   pip install pandas matplotlib seaborn numpy scipy scikit-learn
   ```

3. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook cx36_mut_corr.ipynb
   ```

4. **Run the analysis:**
   - Open `cx36_mut_corr.ipynb` in Jupyter
   - Execute cells sequentially (Cell → Run All) or individually
   - The notebook will generate correlation plots and statistical analyses

### Key Analysis Features

The notebook performs the following analyses:

1. **Data Loading and Processing**
   - Combines FoldX energy output files
   - Processes heterotypic and homotypic mutant configurations
   - Calculates energy differences (ΔΔG) and electrostatic changes (ΔΔΨ)

2. **Statistical Analysis**
   - Silhouette score analysis for functional vs. non-functional separation
   - Linear regression analysis between ESI count and energy terms
   - Mann-Whitney U tests for distribution comparisons
   - Pearson correlation analysis

3. **Visualization**
   - Pairwise scatter plots with silhouette scores
   - ESI vs. ΔΔΨ (electrostatics) correlation plots
   - ESI vs. ΔΔG (total energy) correlation plots
   - Distribution histograms for functional/non-functional mutants
   - Energy component analysis plots

4. **Key Variables**
   - **ESI**: Number of electrostatic interaction pairs
   - **Functional**: Boolean indicating if the mutant forms functional channels
   - **ΔΔG**: Total energy difference from wild-type
   - **ΔΔΨ**: Electrostatic energy difference from wild-type

### Customization

To analyze different structures or configurations, modify these variables in the notebook:

```python
pdb = '8xgd'  # Change to '8iyg' or '8xgd'
file = 'Dif'  # Options: 'Average', 'Dif', 'Raw'
```

---

## Results and Outputs

The notebook generates several publication-quality figures:

- `{pdb}_Pairwise_Plots.svg`: Multi-panel correlation analysis
- `{pdb}_∆Electrostatics_dist.svg`: Distribution of electrostatic changes
- `{pdb}_∆E_vs_∆∆G.svg`: Electrostatics vs. total energy correlation
- `{pdb}_∆Electrostatics_vs_ESI.svg`: ESI vs. electrostatic energy
- `{pdb}_∆∆G_vs_ESI.svg`: ESI vs. total energy

All figures are saved in SVG format for high-resolution publication use.

---

## Citation

If you use this data or code in your research, please cite:

```
Electrostatic Interaction Determines the Docking Specificity and the Formation of Functional Cx36 Gap Junction Channels
RS Wong, Z Song, YT Zheng, H Zhao, D Bai - bioRxiv, 2025
```
