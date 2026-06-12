---
title: "Disable power saving on monitor"
date: 2006-08-21
forum: Desktop Environments
---

### Post by mvip on 2006-08-21
Hi,

I recently installed Ubuntu 6.06 on my old laptop, in order to turn it into an mythtv-machine. Everything worked fine, except for some trouble with the Savage IX card. However, when everything was up running, and I started watching movies on it, I noticed that the monitor constantly went into power saving mode, and I had to move the mouse in order to wake it up.
First thing I did of course, was to **disable the display standby in Gnome**. After that I looked around for console/xorg setting that could effect this. I ended up editing/creating an .Xsession file, that incuded the following commands;
> 
xset -dpms
xset s off
setterm -blank 0 -powersave off powerdown 0

Yet still, the monitor goes into power saving mode.


Anyone got any futher suggestions on how to disable this annoying power saving?

---

### Post by mvip on 2006-08-21
Well, as it turned out, it was the BIOS that overrided the settings , and after disabling powersaving on the monitor in the BIOS, everything worked out fine.

---

