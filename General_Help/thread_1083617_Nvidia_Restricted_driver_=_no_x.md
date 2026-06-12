---
title: "Nvidia Restricted driver = no x?"
date: 2009-03-01
forum: General Help
---

### Post by woosey on 2009-03-01
Hi Guys,

I tried to use the restricted driver for my nvidia 8400GS, however upon rebooting im dropped into the console and i can't seem to get x going, has anyone got round this?

Its ubuntu 8.10 if that helps.

```


root@mythbuntu:/etc/X11# startx
xauth:  creating new authority file /root/.Xauthority
xauth:  creating new authority file /root/.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux mythbuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  1 11:52:39 2009
(==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI
(EE) No devices detected.

Fatal server error:
no screens found
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

---

### Post by woosey on 2009-03-01
Fixed,

My bios was using PCI-E & PCI for the GFX card, i set to PCI-E only and it boots.

---

