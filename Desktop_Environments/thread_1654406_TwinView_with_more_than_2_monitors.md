---
title: "TwinView with more than 2 monitors?"
date: 2010-12-28
forum: Desktop Environments
---

### Post by mclaborn on 2010-12-28
Is it possible to run TwinView with more than 2 monitors.  When I try, it seems to recognize the 3rd monitor, but will allow allow them to be configured as separate X screens.

---

### Post by mclaborn on 2011-01-06
Bump.

---

### Post by Krytarik on 2011-01-06
How do you want to set them up exactly, 3 separate X screens, or all 3 connected to a single virtual desktop?

According to some threads and the Nvidia site itself, it's not possible to use the "TwinView" option to achieve the latter.

---

### Post by mclaborn on 2011-01-07
All 3 on a single desktop.

---

### Post by Krytarik on 2011-01-07
> **mclaborn said:**
> All 3 on a single desktop.
IMO this is only possible with Xorg's build-in "Xinerama" option, and this disables hardware acceleration. You might just try to use TwinView.

How to set up the xorg.conf for each option is explained here:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

Please give feedback if TwinView works this way.

---

