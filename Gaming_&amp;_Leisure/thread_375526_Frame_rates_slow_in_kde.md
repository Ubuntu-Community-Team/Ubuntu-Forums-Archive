---
title: "Frame rates slow in kde"
date: 2007-03-03
forum: Gaming &amp; Leisure
---

### Post by dpar on 2007-03-03
Hi;

I installed the KDE desktop onto my Ubuntu and noticed that games such as GL-117 and Planet Penguin Racer run very jerky under KDE, but run fine in the Gnome desktop. Gl-117 complains about very low frame rates.

Nvidia FX 5200
97xx drivers

Anyone have any ideas as to what the problem is??


Thx  Dave

---

### Post by tgalati4 on 2007-03-03
Try:

glxgears -printfps

In both window managers to see what the baseline framerates are.

Make sure you use the same resolution in KDE as in Gnome.  Drop color from 24-bit to 16-bit.  Sometimes you need to free up video RAM to get 3D to work properly.

KDE uses more video resources and it is possible that it put you over some video memory threshold.  You can turn off all sorts of effects in KDE--turning it into Gnome, effectively.  This may free up video resources to get 3D back.

---

