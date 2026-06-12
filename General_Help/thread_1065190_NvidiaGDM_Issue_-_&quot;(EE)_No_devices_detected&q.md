---
title: "Nvidia/GDM Issue - &quot;(EE) No devices detected&quot; - Intrepid"
date: 2009-02-09
forum: General Help
---

### Post by cjsheets on 2009-02-09
I've enjoyed using Ubuntu for some time now, and only recently have I encountered an issue I haven't been able to resolve. I am having issues getting nvidia drivers to run on a system with 2x9800GT cards. No SLI, and both cards are detected and working.

After a fresh install the X desktop environment works, but I can only use 1 monitor at a low resolution.

I have tried installing the recommended restricted drivers (177) from the built in interface, as well as installing the latest drivers from nvidia's site (180.22) from the command line. Both result in the X server failing to start after a system restart. 

**More Information**
==================================
After a fresh install, my xorg.conf is empty but the main monitor works. running the command *sudo dpkg-reconfigure xserver-xorg* results in an extremely simple, generic xorg.conf being generated.
- - -

switching between the "nv" and "nvidia" drivers by modifying xorg.conf seem to make it switch drivers, but neither fix the problem.
- - -

/var/log/Xorg.0.log reads
```
...
(II) [whichever driver i choose (nv or nvidia)]
(II) Primary Device is:
(EE) No devices detected.

Fatal Server error:
no screens found
```
- - -

sudo startx produces
```
...
(==) using config file: "/etc/X11/xorg.conf"
(EE) No devices detected

Fatal Server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
```
- - -

Any advice would be greatly appreciated.

Regards

---

### Post by singedwings on 2009-02-16
This thread might be of help.

[http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start]("http://ubuntuforums.org/showthread.php?t=1056531&highlight=nvidia+177+unable+start")

---

