---
title: "2560x1600 resolution not working after update to kernel 4.15.0-24"
date: 2018-07-04
forum: Desktop Environments
---

### Post by lglglg on 2018-07-04
Monitor stuck at 1280x1200 resolution after new kernel.

ATI RX 560 card, DELL 3007 monitor, DVI-DVI intel i5-3550, xubuntu 16.04.4.

Tried adding modeline and setting manually with xrandr, no luck.

Works fine with 4.13 kernel.

---

### Post by lglglg on 2018-07-04
Solved, added amdgpu.dc=0 to kernel parameters

---

