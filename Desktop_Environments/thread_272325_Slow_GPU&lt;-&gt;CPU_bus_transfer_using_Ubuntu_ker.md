---
title: "Slow GPU&lt;-&gt;CPU bus transfer using Ubuntu kernel?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by johanseland on 2006-10-06
Hello.

I am one of those guys trying to use the GPU for scientific computations, dubbed GPGPU. I am currently developing on an AMD 64 X2 4200+ using an nForce 4 SLI motherboard, with an Nvidia Geforce 7800 GT GPU

Our application does some readback over the PCI-E, and on this machine we observe slow transfer over the PCI-E bus when it is running Ubuntu Dapper Drake. For one dataset we see 390 "FPS" when it is running Windows (on the very same computer), and 250 "FPS" when running Linux. 

On a similar machine running Gentoo we see comparable speeds to Windows version. 

I suspect this might have something to do with the way the stock Ubuntu kernel is compiled. Is there any tweaks in /proc for tuning bus performance? Should I roll my own kernel?

Any help or tips is appreciated.

---

