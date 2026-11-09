# PhysAR-IDS: evasion and defence evaluation of a smart grid intrusion detector

Code for the paper *PhysAR-IDS* (submitted to IEEE Access): a tuned XGBoost detector for the Sweeten et al. smart grid cyber-physical dataset, evaluated against grey-box (PGD), black-box (PPO) and white-box (tree-greedy) evasion attackers, with adversarial training and an autoencoder gate as defences. A second and a third dataset test whether the findings carry over.

## Scope and responsible use

The attackers work on feature vectors of public datasets. The repository contains no tooling that generates packets or commands for a live system. The code is provided to reproduce the results and to help operators set evasion margins for their own detectors.

## Data

No data are included. Download them from the original sources and place them in `data/` (ignored by git):

| Dataset | Source |
|---|---|
| Sweeten et al. smart grid cyber-physical attack dataset (main) | IEEE Dataport, doi:10.21227/symr-bz19 |
| Morris industrial control system datasets | University of Alabama in Huntsville |
| Digital-substation dataset | Zenodo, doi:10.5281/zenodo.23558261 (v2) |

Check each dataset's licence before redistributing any derived file.

## Layout

| Folder | Contents |
|---|---|
| `notebooks/pipeline_v6/` | Main five-seed pipeline (NB1 to NB15): data and baselines, Optuna tuning, grey-box PGD, black-box PPO, white-box search, budget sweeps, adversarial training, gate, SHAP, cross-dataset runs, ablations, conformal and federated supplements, figures |
| `notebooks/burst_ci_v6b_and_diagnostics/` | Later notebooks that add burst-clustered confidence intervals and diagnostics (white-box NB3c, electrical white-box NB4f, reliance NB4g, derived-feature immunity NB4h, attack F seed check NB4i, defences NB5/NB5b/NB6c) and the second- and third-dataset runs (NB16 to NB18) |
| `notebooks/baseline_v4/` | Earlier v4 baseline notebooks, kept for traceability |
| `results/` | Feature list (93 features: 33 electrical, 60 cyber) |
| `paper/` | Reserved for the accepted manuscript |

Where a notebook appears in both `pipeline_v6/` and `burst_ci_v6b_and_diagnostics/`, the second is the version used for the burst-clustered intervals reported in the paper.

## Running

1. Create an environment and install `requirements.txt` (install `stable-baselines3`, `sb3-contrib` and `gymnasium` with `--no-deps` if installing inside Jupyter would replace your torch build).
2. Set the project and data paths in the first code cell of each notebook; the notebooks were run with local paths and need editing for your machine.
3. Run the notebooks in numeric order. All results use seeds 42, 7, 123, 2024 and 99.

Expect long run times for the PPO and white-box notebooks.

## Citation

Please cite the paper once it is published. Details will be added here.

## Licence

MIT (see `LICENSE`). Datasets keep their own licences.
