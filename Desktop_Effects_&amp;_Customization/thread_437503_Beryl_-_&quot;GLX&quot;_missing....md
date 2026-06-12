---
title: "Beryl - &quot;GLX&quot; missing..."
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by DBGOTD on 2007-05-08
This is what I get when I type in 'beryl'
Any ideas?


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

---

### Post by Pox on 2007-05-09
Try adding ```
Load "glx"
``` under Section "Module" in /etc/X11/xorg.conf.

---

