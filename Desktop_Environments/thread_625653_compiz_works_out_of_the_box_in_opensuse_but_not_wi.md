---
title: "compiz works out of the box in opensuse but not with gutsy gibbon"
date: 2007-11-28
forum: Desktop Environments
---

### Post by nami on 2007-11-28
why is that?  when i click "enable desktop effects" it will not let me.  when i did the equivalent action in opensuse it worked out of the box.

how do i get it to work on my laptop with gutsy gibbon aka ubuntu 7.10? i have a toshiba with a Radeon Mobility M6 LY.

help

---

### Post by cerebellum on 2007-11-28
mine works like charm out of the box. i can't even remember if i installed it. ^_^
have you enabled the restricted video driver?

i'm using acer aspire 2010 with radeon mobility 9700

---

### Post by nami on 2007-11-28
its not in the list as an option in the restricted drivers section...

---

### Post by Cochise on 2007-11-28
open add/remove programs and search for ati tick the box to install the ati xorg driver then try

---

### Post by nami on 2007-11-28
i just tried that and installed the only ati xorg option that came up.  went to restricted drivers and so nothing to do with graphics or ati, restarted and still nothing.  tried desktop effects and still nothing.  how come i dont have any driver option in restricted drivers for my graphics card?

---

### Post by nami on 2007-11-28
the ATI binary X.Org driver doesnt seem to support my card...

ATI binary X.Org driver
Video driver for ATI graphics accelerators 
Video driver for the ATI Radeon and FireGL graphics accelerators.
This version of the ATI driver officially supports:
* FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p
* FireMV: 2200 (Single card PCI-e configuration)
* Mobility FireGL: V5000, T2
* Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, 9800, 9600, 9550, 9500
* Radeon Xpress: 200M series, 1250 IGP, 200 series
* Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500
ATI All-in-Wonder variants of the above cards/chips are also supported, but video capture is not.
This package provides 2D display drivers and hardware accelerated OpenGL.

Canonical Ltd. provides technical support and security updates for ATI binary X.Org driver

---

