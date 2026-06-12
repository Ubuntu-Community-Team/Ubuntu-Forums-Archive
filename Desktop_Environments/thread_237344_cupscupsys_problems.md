---
title: "cups/cupsys problems?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Cloudy on 2006-08-16
[http://i8.tinypic.com/24peazb.png](http://i8.tinypic.com/24peazb.png)

Any time that I attempt to install files via Synaptic or the terminal I get this same error.. I'm not sure what it's all about. It seems like the packages do install, but sometimes with problems and other times it's fine and all. So, what I did was install cups through Synaptic and reboot. Well, I didn't get that error anymore, but now what I get is this:

```
E: cupsys: subprocess post-installation script returned error exit status 3

```

Whenever I try to install things. What's going on? :confused:

---

### Post by Cloudy on 2006-08-16
It's probably also worth noting that this started happening after I removed ubuntu-desktop and started using Kubuntu 6.06 exclusively.

---

### Post by Cloudy on 2006-08-17
Here's some terminal input if it will shed any light:

```

travis@ubuntu:~$ sudo aptitude install cupsys
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  imagemagick libkadm55 libkrb5-dev libkrb53 libmagick9
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up cupsys (1.2.2-0ubuntu0.6.06) ...
 * Starting Common Unix Printing System: cupsd                                                                                               cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on cupsys; however:
  Package cupsys is not configured yet.
dpkg: error processing bluez-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.1.23) | cups (>= 1.1.23); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gimpprint:
 cupsys-driver-gimpprint depends on cupsys-driver-gutenprint (>= 5.0.0~rc2-0ubuntu6); however:
  Package cupsys-driver-gutenprint is not configured yet.
dpkg: error processing cupsys-driver-gimpprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on bluez-cups; however:
  Package bluez-cups is not configured yet.
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on cupsys-driver-gutenprint; however:
  Package cupsys-driver-gutenprint is not configured yet.
 ubuntu-desktop depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 bluez-cups
 cupsys-driver-gutenprint
 cupsys-driver-gimpprint
 hplip
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cupsys (1.2.2-0ubuntu0.6.06) ...
 * Starting Common Unix Printing System: cupsd                                                                                               cupsd: Child exited on signal 15!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on cupsys; however:
  Package cupsys is not configured yet.
dpkg: error processing bluez-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.1.23) | cups (>= 1.1.23); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on bluez-cups; however:
  Package bluez-cups is not configured yet.
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on cupsys-driver-gutenprint; however:
  Package cupsys-driver-gutenprint is not configured yet.
 ubuntu-desktop depends on hplip; however:
  Package hplip is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gimpprint:
 cupsys-driver-gimpprint depends on cupsys-driver-gutenprint (>= 5.0.0~rc2-0ubuntu6); however:
  Package cupsys-driver-gutenprint is not configured yet.
dpkg: error processing cupsys-driver-gimpprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 hplip
 bluez-cups
 cupsys-driver-gutenprint
 ubuntu-desktop
 cupsys-driver-gimpprint
travis@ubuntu:~$     

```

I'm not sure what to do. :( It's apparently hindering me from installing anything now. I tried installing Wine, didn't work. Tried installing ubuntu-desktop, didn't work..

Someone please help? [-o<

---

### Post by Cloudy on 2006-08-17
Well, uninstalling cupsys and all related packages has curbed the problem. I can install software. Unless I'm misunderstanding, cupsys & CUPS just handle printing; I don't even have a working printer, so it shouldn't affect much..

---

