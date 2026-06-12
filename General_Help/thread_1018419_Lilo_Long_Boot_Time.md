---
title: "Lilo Long Boot Time"
date: 2008-12-22
forum: General Help
---

### Post by xquercus on 2008-12-22
I compiled 2.6.27 from source using the following steps:

[https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod](https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod)

My goal is to simply build kernel and header packages with the same config as those distributed with Ubuntu.  That is, I copied the config file distributed with Ubuntu from /boot to .config in my build directory built the packages.

With my newly built packages installed, which should have the same configuration as the packages distributed with Ubuntu, lilo takes a *heck* of a lot longer to load.  It takes several times longer for lilo to complete the "Loading Linux" stage.

My question is why?  What is different about the packages that I built compared to those distributed with Ubuntu to cause lilo to take longer to load?

---

