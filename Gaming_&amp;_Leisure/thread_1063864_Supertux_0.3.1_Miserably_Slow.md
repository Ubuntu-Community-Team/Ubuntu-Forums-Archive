---
title: "Supertux 0.3.1 Miserably Slow"
date: 2009-02-08
forum: Gaming &amp; Leisure
---

### Post by Tsarevich on 2009-02-08
I installed Supertux 0.3.1d on Kubuntu Hardy. It runs at bitterly slow FPS rate. I, as suggested earlier tried to use Radeon driver by adding an attribute under Device section of /etc/X11/xorg.conf like this: Driver "radeon". When I rebooted, the screen started fluctuating and I was forced to remove the line from the file by switching to shell at CTRL + ALT + F2. I ran a search for radeon and learnt that it is a kernel module so I repeated the process by adding the line radeon in /etc/modules. But the same output (ie the fluctuation of screen before KDM appears) was observed. In fact, KDM never appeared. I was dropped to a shell after 3 or 4 fluctuations. And when I press CTRL + ALT + F7, I am dropped to a blank shell again, X doesn't start at all with this configuration. What is the solution? I have Pentium III with 451 MHz frequency and 384 MB RAM.

---

### Post by spadewarrior on 2009-02-08
Hi. What graphics card do you have?

Have you installed the official graphics driver?

---

### Post by Tsarevich on 2009-02-09
ATI Technologies, Inc. 3d RAGE PRO AGP 2X.

Do I use the ATI driver? How do I configure X to use it?

---

### Post by binbash on 2009-02-09
enable the driver of your card and it should run fine

---

### Post by BigSilly on 2009-02-09
Yup. System>Administration>Hardware Drivers should help.

---

