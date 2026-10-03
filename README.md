# M3W: MoE-based Multi-Task World Model (NeurIPS'25)

The official implementation of the paper [Learning and Planning Multi-Agent Tasks via an MoE-based World Model](https://openreview.net/forum?id=fi24ry0BX5), published at [NeurIPS 2025](https://neurips.cc/Conferences/2025)

<p align="center">
  <strong><a href="https://zhaozijie2022.github.io/m3w-marl/">Project Website</a></strong> · <strong><a href="docs/m3w.pdf">Paper PDF</a></strong> · <strong><a href="https://openreview.net/forum?id=fi24ry0BX5">OpenReview</a></strong>
</p>

## Overview
---
**M3W** is a Mixture-of-Experts world model framework for multi-task multi-agent reinforcement learning.

![](docs/images/framework.svg)


M3W leverages the idea of **bounded similarity** in task dynamics, combining **SoftMoE dynamics learning** and **SparseMoE reward prediction** within a world model. By planning directly on predicted rollouts with a **multi-agent MPPI planner**, it enables efficient knowledge reuse, conflict avoidance, and scalable multi-task adaptability, surpassing policy-centric approaches.

![](docs/images/method.svg)

<!-- ### 📑 Table of Contents
1. [Installation](#installation)  
2. [Quick Start](#quick-start)  
3. [Results](#results)  
4. [Acknowledgement & Citation](#acknowledgement--citation) -->

---
## ⚙️ Installation
```bash
conda create -n m3w python=3.8 -y
conda activate m3w
pip install -r requirements.txt
```
If you encounter issues when installing **MA-MuJoCo**, **Isaac Gym** or **Bi-DexHands**, please refer to [MA-MuJoCo](https://github.com/schroederdewitt/multiagent_mujoco), [Isaac Gym](https://developer.nvidia.com/isaac-gym) and [Bi-DexHands](https://github.com/PKU-MARL/DexterousHands).

## 🚀 Quick Start
For training, please run:
```bash
python examples/train.py --load_config configs/mujoco/installtest/m3w/config.json
```
You can modify the configuration in `configs/mujoco/installtest/m3w/config.json` to customize the training process.

We extend Bi-DexHands to multi-task settings using multiprocessing, which makes the sampling process significantly slower. To accelerate training, you can refer to the settings in [shadow_hand_meta settings](https://github.com/PKU-MARL/DexterousHands/tree/main/bidexhands/tasks/shadow_hand_meta) and enable GPU-based parallel multi-task execution.


## 📈 Results

M3W achieves superior performance on both Bi-DexHands and MA-MuJoCo, showing superior sample efficiency and multi-task adaptability compared to policy-centric baselines.

![](docs/images/compare.png)

## 🎥 Demos
Here we showcase several representative task rollouts demonstrating the diverse cooperative behaviors learned by M3W.

#### Bi-DexHands
<p align="center">
  <img src="docs/demos/dex/over.gif" alt="Over" width="16%"/>
  <img src="docs/demos/dex/catch-abreast.gif" alt="Catch Abreast" width="16%"/>
  <img src="docs/demos/dex/catch-underarm.gif" alt="Catch Underarm" width="16%"/>
  <img src="docs/demos/dex/lift-underarm.gif" alt="Lift Underarm" width="16%"/>
  <img src="docs/demos/dex/open-outward.gif" alt="Open Outward" width="16%"/>
  <img src="docs/demos/dex/scissors.gif" alt="Scissors" width="16%"/>
</p>

#### MA-MuJoCo
<p align="center">
  <img src="docs/demos/mujoco/crf.gif" alt="Cheetah Run Front" width="16%"/>
  <img src="docs/demos/mujoco/crun.gif" alt="Cheetah Run" width="16%"/>
  <img src="docs/demos/mujoco/hop.gif" alt="Hopper Hop" width="16%"/>
  <img src="docs/demos/mujoco/runbwd.gif" alt="Cheetah Run Backward" width="16%"/>
  <img src="docs/demos/mujoco/rh.gif" alt="Reacher" width="16%"/>
  <img src="docs/demos/mujoco/wkst.gif" alt="Walker Stand" width="16%"/>
</p>

## 🙏 Acknowledgement & 📜 Citation
Our code is built upon [HARL](https://github.com/PKU-MARL/HARL), [TDMPC2](https://github.com/nicklashansen/tdmpc2) and [Light-SoftMoE](https://github.com/zhaozijie2022/soft-moe). We thank all these authors for their nicely open sourced code and their great contributions to the community.

If you find our research helpful and would like to reference it in your work, please consider the following citations:

```bibtex
@inproceedings{zhao2025m3w,
  title     = {Learning and Planning Multi-Agent Tasks via an MoE-based World Model},
  author    = {Zhao, Zijie and Zhao, Zhongyue and Xu, Kaixuan and Fu, Yuqian and Chai, Jiajun and Zhu, Yuanheng and Zhao, Dongbin},
  booktitle = {Advances in Neural Information Processing Systems},
  year      = {2025}
}
```
