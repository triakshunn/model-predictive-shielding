# Model Predictive Shielding

Implementation of the model predictive shielding algorithm from [Model Predictive Shielding for Safe and Efficient Reinforcement Learning](https://arxiv.org/abs/1905.10691).

## Overview

This repository demonstrates safe reinforcement learning using model-predictive shielding on CartPole and Bicycle environments. The shield switches between:
- **Learned policy**: Neural network trained with BPTT
- **Recovery policy**: Trained to return to safe states
- **LQR policy**: Locally optimal stabilizing controller

Safety is guaranteed by model-predictive verification at each timestep.

## Requirements

- Python 3.6+
- Dependencies: `numpy`, `pytorch`, `gym`, `sklearn`
- MATLAB (optional, for LQR verification): SOSTOOLS 3.03, SeDuMi

```bash
pip install numpy torch gym scikit-learn
```

## Installation

### Using Conda (recommended)
```bash
conda env create -f environment.yaml
conda activate model_pred_shielding
```

### Using pip
```bash
pip install -r requirements.txt
```

## Quick Start

### Train Policies
```bash
cd python
python -m spire.main.cartpole_train
```

### Test with Shield
```bash
python -m spire.main.cartpole_test
```

### Run Baseline (requires Z3)
```bash
cd baseline/python
python main.py
```

## Results

Typical CartPole results (100 episodes, 200 steps):
- **Safety probability**: 1.0 (100% safe)
- **Learned policy usage**: 90-98% (after convergence)
- **Final cart position**: ~0.33 m

## Project Structure
