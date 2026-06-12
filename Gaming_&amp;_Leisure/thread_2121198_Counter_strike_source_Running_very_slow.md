---
title: "Counter strike source Running very slow"
date: 2013-03-01
forum: Gaming &amp; Leisure
---

### Post by Hex9 on 2013-03-01
Hi,

Installed Steam for Linux not too long ago but have trouble playing cs, 

All my games ran fine in Windows 7, 500fps+ but in ubuntu im getting approx 20fps, wondering if i need to install a graphics driver or openGL?

I've used sudo apt-get update & upgrade but no solution

Thanks :)

Hardware is i7 2600k, 6970 etc...

---

### Post by kaldor on 2013-03-02
CS:S runs beautifully for me on slower hardware than yours. 

I assume that you're using the AMD Open Source driver (default). The benefit to this driver is that it integrates very well and is solid. Sadly, it's very slow for most 3d purposes and definitely won't suffice for actual competitive gaming. It also lacks certain features like power management.

The solution is to install the AMD proprietary driver (fglrx). This driver is very fast, but it does bring instabilities. It may add tearing, input delays, and slow 2d performance. Install this driver via the Additional Drivers dialog in Software Sources. 

My recommendation to you is to use NVIDIA graphics if you intend to do any gaming on Linux. The NVIDIA proprietary driver is very stable and works about as well as it does on Windows (sometimes better, sometimes worse). It also makes WINE gaming smoother due to certain NVIDIA-specific optimizations.

---

### Post by vasilenko93 on 2013-03-02
I am running CS Source as fast as in Windows(1680 x 1050, max graphics), I have an ATI Radeon HD 5670(old btw) with ATI/AMD proprietary FGRX graphics drivers. So all I recommend is installing the right drivers.

---

### Post by deri on 2013-03-03
I have easily 100+ fps Not that modern computer with 4x3800mhz amd, 7770 ati. And almost all quality settings maximum.

---

### Post by Hex9 on 2013-03-03
I reinstalled the proper graphics drivers from amd. If you're have the same problem i suggest following the suggestions found [here]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx")

The game runs very well now

---

### Post by kaldor on 2013-03-04
Thanks for reporting back :)

Good to know everything worked out for you.

---

### Post by glln0v on 2013-03-05
Anybody using Intel HD4000 Ivy Bridge graphics? Is the built-in stuff good enough yet that we can get good performance from it for game like CS:source?

---

### Post by kaldor on 2013-03-05
> **glln0v said:**
> Anybody using Intel HD4000 Ivy Bridge graphics? Is the built-in stuff good enough yet that we can get good performance from it for game like CS:source?

Intel HD 4000 graphics should be able to play CS:S on very low settings. It won't be optimal but it should work. I don't have Intel graphics, so take this with a grain of salt.

Since Intel uses only open source drivers on Linux be sure to be using the most recent graphics stack possible. You may need to enable certain features for optimal performance. 

Alternatively you can give CS 1.6 a try if Source is too heavy for your hardware.

---

