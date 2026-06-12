---
title: "Blank screen on graphical login"
date: 2007-09-17
forum: Desktop Environments
---

### Post by nish.des on 2007-09-17
Hello,

Could someone please tell me where the Xclient scripts (as in "Run Xclient scripts" session in graphical login) are kept?

A friend of mine keeps getting a blank screen after login in this default session. The only thing that seems to work is the xterm failsafe session (even gnome failsafe doesnt work). I have tried sudo dpkg-reconfigure xserver-xorg, it does not work. The problem surfaced all of a sudden as far as I know, no changes in configuration were made and no new hardware added.

In the failsafe session (where no window manager is loaded and all "windows" are just squares on the screen without any window-like decoration (borders, titlebar etc.) But I can manually launch gnome-panel from the xterm. Running beryl from the panel restores all 3D effects (which I have afterwards temperorily disabled and set the manager to metacity) and also all window decoration, but still no desktop.

On rebooting, the same problem continues.

Any idea as to what the problem could be? In any case, please help me wih the location of these scripts.

Regards,
Nishita.

---

