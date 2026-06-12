---
title: "No composite extension"
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by lxstoian on 2007-08-09
I get this when i try to start beryl :
No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

How can i fix this?

---

### Post by EclipseAgent on 2007-08-09
> **lxstoian said:**
> I get this when i try to start beryl :
No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

How can i fix this?

You need to add compisite enabled in your xorg.conf


Section "Extensions"
  Option       "Composite" "Enable"
EndSection

---

### Post by iAndrew on 2007-08-09
If it doesn't work right away, reboot or restart gdm.

---

