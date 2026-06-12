---
title: "icons missing for pcmanfm"
date: 2007-11-10
forum: Desktop Environments
---

### Post by chocolatetoothpaste on 2007-11-10
Hi everyone,
  I am piecing together an openbox system from scratch.  Everything is going great, except, I installed pcmanfm, and there are no icons.  I get a message that says:

GTK+ icon theme is not properly set

This usually means you don't have an XSETTINGS manager running.  Desktop environments like GNOME or XFCE automatically execute their XSETTINGS managers like gnome-settings-daemon or xfce-mcs-manager.

> 
If you don't use these desktop environments, you have two choices:
1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in you ~/.gtkrc-2.0.
(create if no such file)

NOTICE: The icon them you choose should be compatible with GNOME, or the file icons cannot be displayed correctly.  Due to the differences in icon naming of GNOME and KDE, KDE themes cannot be used.  Currently there is no standard for this, but it will be solved by freedesktop.org in the future.



So, by my guess, method 2 will be the lowest impact on my system.  I can create ~/.gtkrc-2.0 easy enough, and I can assign an icon theme as per the directions given.  But here's my question, where/how do I install an icon theme?

---

### Post by jseiser on 2008-01-02
Extract to ~/.icons or /usr/share/icons

---

