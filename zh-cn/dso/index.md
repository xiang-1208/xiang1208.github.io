# DSO


# Direct Sparse Odometry：直接稀疏里程计

<!--more-->

**摘要**：我们提出了一个新颖的直接稀疏里程计方法（DSO）。整个系统结合了一个完全直接的概率模型（最小化光度误差），并对所有的模型参数进行优化，包括在参考帧中表示为反深度的几何图形和相机运动。为了达到实时运算，算法去除了直接法添加先验的做法，取而代之的是从整个图像上均匀的采样关键点。因为我们的方法不依赖关键点检测或描述符，所以它可以自然地从所有具有强梯度的图像区域中采样像素，包括边缘或平滑的光度变化区域（大多在白色墙壁）。该模型集成了一个完整的光度校准，包括曝光时间、透镜光晕和非线性响应函数（这些基本上都是相机的参数）。我们在三个数据集，包括几个小时的视频上全面评估了我们的方法。实验表明，在各种现实环境下，该方法在跟踪精度和鲁棒性方面都显著优于最先进的直接和间接方法。

# 1. 引言

&emsp;&emsp;同时定位和建图（SLAM）和视觉里程计（VO）是许多新兴技术的基本组成部分——从自动驾驶汽车和无人机到虚拟现实和增强现实。近年来，SLAM和VO的实时方法取得了重大进展。虽然长期以来该领域由基于特征的（间接）方法主导，但近年来，许多不同的方法越来越受欢迎，即直接和密集方法。

**直接 vs. 间接**
