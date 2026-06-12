---
title: "Gnome Detects Monitor, xorg.conf empty"
date: 2008-12-31
forum: General Help
---

### Post by norica on 2008-12-31
GNOME detects my HP Pavilion mx703 monitor with my ATI Radeon 9250 graphics card. GNOME provides me with a nice resolution.

However, xorg.conf is still generic, showing nothing about my Pavilion mx703.

This is a problem for since I like using Fluxbox, and when I switch from GNOME into Fluxbox my resolution goes back down to 800x600.

I have already tried 'sudo dpkg-reconfigure xserver-xorg' to no avail.

---

### Post by pytheas22 on 2008-12-31
In Ubuntu 8.10, X tries to auto-detect everything on-the-fly, rather than referring to the settings specified in xorg.conf.  This is probably why your file is mostly empty.  However, you should still be able to specify monitor resolution and have X use it.

[This thread]("ubuntuforums.org/showthread.php?t=83973") has instructions on how to set an explicit screen resolution in xorg.conf.  Please try following it.  Remember that you need to restart X for changes to take effect; please also be sure to back up your existing xorg.conf just in case.

Also, if you have an older xorg.conf (from an earlier version of Ubuntu perhaps, or one that you could obtain by booting to the live CD of an older version), you could probably just copy that.

---

