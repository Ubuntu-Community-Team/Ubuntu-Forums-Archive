---
title: "KDE 640x480 screen on bootup, restarting X fixes it temporarily"
date: 2008-11-05
forum: Desktop Environments
---

### Post by Wiccanpiper on 2008-11-05
I'm running Kubuntu 8.10, GeForce 5200, and nVidia 173 drivers.  This last time I completely deleted all the 173 drivers, shutdown, and then installed them again with Envy.  Still got the same problem:

On first boot, the system boots into 640x480 mode.  I log in, and then restart X  with ctrl-alt-backspace.  Then, I get my normal 1680x1050 screen, and Nvidia Config Tool reports the correct  monitor.  If I run the Config Tool while in 640x480 mode, it shows generic monitor and I can't change resolution at all.  My xorg.conf is the generic one that's installed when you install Ibex.

Tried sudo dpkg-reconfigure xserver-xorg, and that didn't help.

Anyone got a clue how to fix this so I don't have to restart X every time?  Thanks!

---

