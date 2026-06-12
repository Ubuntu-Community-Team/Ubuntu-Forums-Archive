---
title: "Kubuntu System Settings Dsiplay Problem"
date: 2006-09-04
forum: Desktop Environments
---

### Post by indytim on 2006-09-04
I've recently installed the Kubuntu desktop along with my pre-existing Dapper Gnome desktop.  On setting up the desktop, I've run into a problem when I try to reduce the screen resolution.  It is currently set at the max of 1600x1200.  When accessing 

System Settings -> Display

The slider bar for adjusting the resolution is "greyed out".  I have entered my user password to access the Administrative mode and it has no effect.  A quick try at some of the other options in the System Settings appears that other utilities are functional.

Any idea's??

Thanks,

IndyTim

---

### Post by halfvolle melk on 2006-09-04
Hi IndyTim,
You could try to run
```
sudo dpkg-reconfigure xserver-xorg
```
from a terminal. Somewhere in there it will ask for what screen res. to support and what not to support. Also, you may need to manually edit /etc/X11/xorg.conf and look for this section:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       27-96
        VertRefresh     50-160
```
Make it so that it's right for your monitor.

---

