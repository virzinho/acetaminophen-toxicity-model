# Modeling the Biochemical Threshold of Acetaminophen Toxicity

An academic project by **Fabio Virzi**, MSc student in Artificial Intelligence for Biomedicine and Healthcare, University of Turin.

The project explores a three-equation model of acetaminophen metabolism, formation of the reactive metabolite NAPQI, and glutathione depletion. It combines Michaelis-Menten elimination with an oxidative pathway and numerical integration in Python.

**Project status:** original coursework with a subsequent numerical review. The review identifies a unit-conversion error in the submitted notebook. Correcting that conversion changes the simulated glutathione response substantially, so the original quantitative toxicity-threshold claims are not supported by the corrected calculation. The original report and notebook are retained unchanged for transparency.

## Contents

- [Original report](reports/acetaminophen_toxicity_report.pdf): the submitted 19-page academic report.
- [Original notebook](notebooks/acetaminophen_toxicity_original.ipynb): the submitted notebook, including its original plots and outputs.
- [Numerical review](docs/NUMERICAL_REVIEW.md): unit conversion, parameter consistency and interpretation limits.
- [Unit-conversion comparison](scripts/compare_unit_conversion.py): reproduces the original and conversion-corrected baseline simulations without changing the submitted files.
- [Comparison results](results/unit_conversion_comparison.json): numerical output from the verification run.

## Topics explored

- Saturable elimination compared with an exponential approximation.
- Acetaminophen, NAPQI and glutathione time courses.
- A sweep over initial acetaminophen concentrations and a glutathione-depletion criterion.
- Illustrative changes to metabolic parameters and baseline glutathione reserves.
- A simplified NAC intervention implemented as changes to synthesis and consumption terms, rather than a dose-resolved NAC pharmacokinetic model.

These are simulated scenarios, not measurements from patients or validated predictions of treatment response. No clinical dataset was used for model fitting or external validation. This repository does not provide dosing or treatment recommendations.

## Reproduce the numerical review

Tested with Python 3.12, NumPy, SciPy and Matplotlib.

```bash
python -m venv .venv
# Linux/macOS: source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python scripts/compare_unit_conversion.py
```

The script writes `results/unit_conversion_comparison.json`. It uses the equations and default integration settings extracted from the original notebook, changing only the NAPQI-source conversion in the corrected comparison.

To reproduce all original plots, run:

```bash
python scripts/run_original_notebook.py
```

This executes the original notebook code in `results/original_run/` and preserves its original modelling assumptions and labels. Alternatively, open the notebook in Jupyter or Google Colab.

## Interpretation and next steps

The primary value of this project is practice in translating biochemical hypotheses into differential equations, implementing simulations, checking assumptions and interpreting sensitivity. The conversion review demonstrates why numerical execution alone does not establish scientific validity.

Further development would require consistent concentration compartments and reaction stoichiometry, justified parameters, uncertainty analysis, and comparison with independent experimental or clinical data. The current comparison is a dimensional correction, **not a validated replacement model**.

## Provenance

The PDF and notebook are the original author-supplied coursework. Repository organisation, documentation and the separate unit-conversion verification script were prepared with AI assistance. The original numerical model was not silently rewritten. References cited in the coursework should be checked against their primary sources before its parameter values are reused.
