---
title: "Applications high load when running on external display"
date: 2014-07-24
forum: Desktop Environments
---

### Post by mctiew on 2014-07-24
I have been having this problem with running application using external ( VGA ) display.

The behaviour on this is like this :-

1. Hardware is dell E6410 with an intel graphic display. 
2. 8 GB RAM.
3. OS is Ubuntu 14.04.. But also experience it on other OS. So don't think it's specific to OS.
4. When running on inernal notebook display (eDP1), everything is smooth and low CPU utilization.
5. But when running on external VGA1 display, these process will use more CPU: firefox, xorg, plugin-container, compiz/xfwm4, virtualbox, VMware workstation etc etc. If I only run a few applications, maybe the CPU is enough. But as soon as I running more CPU intensive applications such as virtualbox or VMware, the system will slow down to a unusable state. Sometime with only firefox, the system can already be pretty sluggish. 

I hope to get some feedback from this problem which could lead to some further isolation or investigation to this problem. I tend to this is the xorg/intel graphic driver problem. But I can't say for sure.

Any input ?

---

