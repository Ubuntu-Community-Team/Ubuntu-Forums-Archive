---
title: "KDE cannot connect to the internet"
date: 2011-04-30
forum: Desktop Environments
---

### Post by dragonwrenn on 2011-04-30
I'm unable to connect the internet while running KDE desktop on Ubuntu 10.10.

Neither Rekonq nor Chrome can connect to the internet.  I recently moved to KDE from GNOME, and I uninstalled all GNOME packages via Synaptic.
I'm trying to connect with a cable and it worked fine in GNOME, but not KDE.

I'm also dual-booting Windows and Ubuntu, and can connect fine from Windows without changing anything, so it must be a software issue on the KDE side.


(I don't know if this is actually relevant), but it says in System Settings/Service Manager that Network Watcher (in Load-On-Demand-Services) is not running.  It doesn't start running when I try to connect to the internet. 

Thanks!

---

### Post by bergfly on 2011-05-03
How did you move to KDE, which packages did you install. Do you have a network icon in the system tray? You might be missing packages. Make sure you have plasma-widget-networkmanagement installed. That should give you the icon in the system tray. 

If that is not the issue then there is a bunch of troubleshooting we need to do.

Installing package wicd will give you network connectivity too.

---

