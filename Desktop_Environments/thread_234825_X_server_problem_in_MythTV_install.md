---
title: "X server problem in MythTV install"
date: 2006-08-12
forum: Desktop Environments
---

### Post by AngryMallard on 2006-08-12
So I'm trying to install MythTV on a 1.3 gHz Pentium 4 eMachines desktop with Nvidia based on [this guide]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation") and when I restarted, all of a sudden I get the message "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" then when I choose "Yes"

```
X Window System Version 7.0.0
Release Date:21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux emachines-ubuntu 2.6.15-26-686 #1 SMP PR
Build Date: 16 Marchin 2006
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg/0.log", Time: Sat Aug 12 03:12:10 2006
(==) Using config file: "/etc/X11/xorg.conf"
(WW) NVIDIA: No matching Device section for instance (BusID PCI:3:0:0) f
(EE) No devices detected.

Fatal server error:
no screens found

```

Or is there a way to just reload/reinstall/restart X?

---

