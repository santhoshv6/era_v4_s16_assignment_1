# GridWorld Value Function (4×4)

This repository contains a Jupyter notebook that computes the state-value function \(V(s)\) for a 4×4 GridWorld under a **uniform random policy** (each action chosen with probability 0.25).  
Rewards are \(-1\) for each action step, the terminal state (bottom-right) is absorbing with reward/value 0, \(\gamma = 1\) (no discounting), and the iterative updates stop once the maximum change in \(V\) drops below \(1e{-4}\).

---

## Contents
- `GridWorld.ipynb` — notebook that runs end-to-end and prints the converged value function.

---

## Environment details
- Grid size: 4×4 with 16 states (0 to 15), laid out row-major.
- Start state: top-left (state 0).
- Terminal state: bottom-right (state 15), fixed at value 0.
- Actions: Up, Down, Left, Right with equal probability \(0.25\).
- Boundary handling: actions that would go out of bounds keep the agent in the same state.
- Reward model: \(-1\) for each action attempt; terminal returns 0.

---

## Method
The notebook performs iterative Bellman expectation updates (policy evaluation) for the uniform random policy.

For each non-terminal state \(s\):
\[
V_{\text{new}}(s) = \frac{1}{4}\sum_{a \in \{\uparrow,\downarrow,\leftarrow,\rightarrow\}} \left[r(s,a) + \gamma V(s')\right]
\]
with \(\gamma = 1\) and \(s'\) computed using boundary-safe transitions.

Convergence is detected when:
\[
\max_s |V_{\text{new}}(s) - V(s)| < 1e{-4}
\]

---

## How to run
### Option A — Local laptop
1. Open `GridWorld.ipynb` in Jupyter (VS Code / Jupyter Lab / Jupyter Notebook).
2. Run **all cells** from top to bottom.

### Option B — Google Colab
1. Upload `GridWorld.ipynb` to Colab.
2. Runtime → Run all.

---

## Output (captured)
- Iterations: `471`
- Last max delta: `9.891255676564015e-05`

Final value function \(V\) (reshaped to 4×4):

[[-59.42367735 -57.42387125 -54.2813141 -51.71012579]
[-57.42387125 -54.56699476 -49.71029394 -45.13926711]
[-54.2813141 -49.71029394 -40.85391609 -29.99766609]
[-51.71012579 -45.13926711 -29.99766609 0. ]]

text