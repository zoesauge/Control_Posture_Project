# Postural Control Model – Group D

Mathematical Modeling final project – Master IEAP, Université de Montpellier (2026)

**Authors:** Jeanne Le Roux and Zoé Sauge

## Project

We study a simple first-order model of postural control, where the body pivots around the ankles and θ is the lean angle from the vertical:

dθ/dt = f(θ) = α sin θ − βθ − γ

- α sin θ: gravity (amplifies the lean)
- −βθ: postural correction (reduces the lean)
- −γ: constant bias (set to 0 in this study)

With α = 2 s⁻¹ and γ = 0, we compare a strong correction (β = 2.4 s⁻¹) and a weak correction (β = 1.99 s⁻¹).

## Contents

| File / folder | Description |
|---|---|
| `Questions_code.ipynb` | Full notebook: model, Q2 to Q4 and validation |
| `figures/` | Figures used in the report (created when the notebook runs) |

Notebook structure:
1. **Setup** – parameters and model function `posture_rhs`
2. **Q2** – plot of f(θ), equilibria and stability (β = 2.4)
3. **Q3** – explicit Euler simulations from θ(0) = ±0.08 rad over 600 s (h = 0.05 s)
4. **Q4** – same study with weaker feedback (β = 1.99)
5. **Extra** – validation of the time step (h = 0.05 s vs h = 0.01 s)

## How to run

Requirements: Python 3 with `numpy` and `matplotlib`.

    pip install numpy matplotlib

Open `Questions_code.ipynb` (VS Code or Jupyter) and run all cells in order. Figures are saved in `figures/`.

## Main results

- **β = 2.4 > α:** the upright posture (θ = 0) is the only equilibrium and is stable; the body returns to the vertical in about 10 s.
- **β = 1.99 < α:** the upright posture becomes unstable and two stable leaning postures appear at θ ≈ ±0.173 rad (about 10°), reached after a slow drift of several minutes (pitchfork bifurcation).
- Reducing the time step does not change the results (max difference 2.4 × 10⁻⁴ rad), so h = 0.05 s is sufficient.
