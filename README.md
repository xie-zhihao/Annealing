# Ising-Type Prediction Toolkit

> A modular simulation toolkit for classical spin systems, covering **two model families** (Ising and RKKY long-range generalizations) and **four algorithms** (each runnable with **annealing** or at a **fixed temperature**). Designed for phase-transition studies and cross-disciplinary applications.

## Authors

**Zhihao Xie**¹\* · **Chenran Kang**² · **Tin Htoo**² · **Joey Wat**²˒³ · **Julia Corrales**² · **Thomas Hallal**¹˒²  
¹ Department of Mathematics, University of California, Berkeley, CA 94720, USA  
² Department of Physics, University of California, Berkeley, CA 94720, USA  
³ Department of Physics, The Hong Kong University of Science and Technology, Clear Water Bay  
\*Corresponding Contact: **xiezhihao-justin@berkeley.edu** · **xiezhihao2021@foxmail.com**

---

## 1. Overview

This toolkit provides a unified environment for simulating and analyzing Ising-type models from the baseline 2D nearest-neighbor system to long-range RKKY-coupled variants. It implements multiple Monte Carlo strategies with optional annealing schedules, enabling quantitative studies of energy, magnetization, susceptibility, heat capacity, and critical exponents. It also supports side-by-side algorithm comparisons near criticality and in rugged energy landscapes.

**Benchmarks (2D Ising)**  
- Critical temperature `\(T_c \approx 2.269\)`  
- Critical exponents `\(\beta = 0.125 \pm 0.003\), \(\gamma = 1.75 \pm 0.05\)`



**Algorithmic takeaways**  
- **Swendsen–Wang**: best efficiency near \(T_c\) (mitigates critical slowing down).  
- **BSAISA**: robust convergence from disordered initial states and rough landscapes.  
- **Metropolis**: solid baselines; performance degrades near \(T_c\) without clustering.
- **Heat Bath**: solid baselines; performance degrades near \(T_c\) without clustering.

---

## 2. Model Families

### 2.1 Ising (baseline)
- Dimensions: 1D / 2D / 3D (2D nearest-neighbor by default)  
- Spins: \(\sigma_i \in \{+1, -1\}\)  
- Interactions: nearest-neighbor coupling; optional external field

### 2.2 RKKY long-range generalizations
- Oscillatory long-range coupling:
  \[
  J_{ij} = A \cdot \frac{\sin(2 k_F R_{ij})}{(2 k_F R_{ij})^2},
  \]
  where \(R_{ij}\) is pair distance and \(k_F\) the Fermi wavevector.  
- Features: competing interactions → **frustration** and multi-valley energy landscapes  
- Implementation: distance cutoff \(D_{\text{cut}}\) to balance accuracy and cost

---

## 3. Algorithms (annealing or fixed-T modes)

1. **Metropolis**  
   Acceptance \(P = \min\{1, e^{-\Delta E/T}\}\); minimal and reliable baseline.

2. **Heat Bath**  
   Direct sampling from local-field conditionals; mixes quickly in homogeneous regions.

3. **Swendsen–Wang (cluster)**  
   Build and flip correlated clusters; substantially reduces critical slowing down (compute/memory trade-offs apply).

4. **BSAISA** — *Backtracking Search Algorithm Inspired by Simulated Annealing*  
   Adaptive backtracking with annealing-style exploration; robust for disordered starts and rugged landscapes.

---

## 4. Methodology & Observables

- **Initialization**: random or structured configurations on an \(L \times L\) lattice (higher-D supported)  
- **Evolution**: apply chosen update rule; optional temperature schedules (annealing/tempering/adaptive)  
- **Measured quantities**: energy \(E(T)\), magnetization \(M(T)\), susceptibility \(\chi(T)\), heat capacity \(C(T)\), Binder cumulants, autocorrelation times  
- **Critical analysis**: finite-size scaling to estimate \(T_c\), \(\beta\), \(\gamma\) with uncertainty

---

## 5. Applications

- **Boltzmann Machines / Hopfield Neural Networks** (energy-based modeling, memory retrieval)  
- **Liquid–Gas** analogies (order parameters and phase behavior)  
- **Turbulence** (critical-phenomena-inspired diagnostics for complex flows)  
- **Market Crash & Stock Index Prediction** — based on **agent-based Bornholdt models**

---

## 6. Workstreams

1. **Baseline Ising**: benchmarks across dimensions, boundary conditions, and lattice sizes  
2. **Long-range & Disorder**: RKKY, dilute/impure alloys, glassy variants, and frustration  
3. **Algorithm Engineering**: hybrid cluster/local updates; adaptive schedules; BSAISA refinements  
4. **Finite-Size Scaling**: standardized pipelines for \(T_c\) and critical exponents with error bars  
5. **Visualization & Diagnostics**: real-time curves, peak finding, cumulant crossings, autocorrelation analysis  
6. **Applications**: magnetocaloric estimates, optimization mappings, financial agent-based experiments  
7. **Extensibility**: higher dimensions, external fields, quantum-inspired extensions, heterogeneous computing

---

Maintainer: Zhihao
