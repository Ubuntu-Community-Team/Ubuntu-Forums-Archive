---
title: "Display fuzzy after suspend"
date: 2022-10-17
forum: Desktop Environments
---

### Post by svenole on 2022-10-17
Newly installed 22.04 on old Apple iMac with ATI Mobility Radeon HD 2600 XT/2700 graphics card. Kernel version is 5.15.0-50-generic and I`ve installed the Radeon driver amdgpu-install_5.3.50300-1_all. 

The trouble is that the display gets fuzzy after suspend. It gets blurry, but it is possible to read and see what is going on so that I can reboot. I`ve tried several things to kind of restart the display (change resolution etc) without luck. 

Any clues on how to fix this issue? 

Brgds, 

- Sven

---

### Post by svenole on 2022-10-17
I realized that I did not really install the AMDGPU driver so the thing is that it is the default graphics driver in Ubuntu 22.04.1 LTS that makes my display disorted after a suspend. I did install the AMD Radeon driver, but this did not work at all. The display got fuzzy already at boot time and even when booting in single user mode, so I struggled a bit to uninstall it. 

Anyway - I still wonder if someone have experienced this display behavior after suspend with an ATI Radeon based computer running 22.04.01 LTS. 

- Sven

---

