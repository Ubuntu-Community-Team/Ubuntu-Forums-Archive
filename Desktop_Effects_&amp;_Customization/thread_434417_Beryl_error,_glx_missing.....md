---
title: "Beryl error, glx missing...."
date: 2007-05-05
forum: Desktop Effects &amp; Customization
---

### Post by searayman on 2007-05-05
i try and start bery and here is my error:

mike@mike-desktop:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
mike@mike-desktop:~$

---

### Post by kiddyfurby on 2007-05-06
make sure you have these two lines in your xorg.conf, device section
    Option         "AddARGBVisuals"     "True"
    Option         "AddARGBGLXVisuals"  "True"

---

