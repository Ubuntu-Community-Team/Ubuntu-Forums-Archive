---
title: "Why different kernels?"
date: 2022-04-04
forum: Desktop Environments
---

### Post by thumper76 on 2022-04-04
I have two computers running Ubuntu 20.04.4 LTS. One is a desktop and one is a laptop, not that it should matter. Both are set for auto updates. However they have different kernels.
The desktop is 5.13.0-39 generic and the laptop is 5.14.0-1031-oem. Why the difference?

---

### Post by TheFu on 2022-04-04
Because there are different repos configured in each?

---

### Post by ActionParsnip on 2022-04-04
Its a conscious effort to install different kernels. You have different package sources enabled

---

### Post by grahammechanical on 2022-04-04
The laptop does not have a Ubuntu generic kernel but a Ubuntu oem kernel. Read about it here:

[https://wiki.ubuntu.com/Kernel/OEMKernel](https://wiki.ubuntu.com/Kernel/OEMKernel)

Regards

---

### Post by guiverc on 2022-04-04
Ubuntu offers two primary kernel stack choices for LTS releases.

**GA** = general kernel; the most stable & default for Ubuntu Server installs

**HWE** = hardware enablement stack; which upgrades from the GA (20.04 & 20.04.1) to 20.10's kernel at 20.04.2, 21.04's kernel at 20.04.3, 21.10's kernel at 20.04.4 (ie. the 5.13 kernel you list) and will use the 5.15 kernel at 20.04.5

For more details of GA vs HWE see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

For *flavors* & desktop installs, and releases prior to 20.04, the ISO used to install controlled which kernel stack you used; installs of 20.04 & 20.04.1 media use GA (*for flavors*) and 20.04.2 media & later uses HWE.  This applied to Ubuntu 18.04, 16.04 & earlier too for Ubuntu, but starting with Ubuntu 20.04 LTS Desktop the default for all media is HWE.

**Further** to that, if you install with a desktop ISO and your hardware is detected to benefit from an **OEM** kernel, that will be used instead. Ubuntu Desktop media contains these OEM kernels, but some *flavors* do not have them. See link provided by @grahmechanical

Thus a Ubuntu 20.04 LTS  system can exist using different kernels, GA (5.4), HWE (*currently* 5.13) or OEM (*varies on hardware*); you list systems with 2 of these 3 kernel stack options.

---

