---
title: "omap / pandaboard: always problems with Xorg"
date: 2011-10-06
forum: Desktop Environments
---

### Post by schenkelklopfer on 2011-10-06
hi, i have problems with my pandaboard, getting the graphic to run...

sometime it's working, sometimes not....

if i try this on the shell via ssh:
user@pandaboard:~$ sudo Xorg -config xorg.conf.new -retro

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.35-22-omap armv7l Ubuntu
Current Operating System: Linux pandaboard 2.6.38-1208-omap4 #11-Ubuntu SMP PREEMPT Fri Apr 15 16:34:35 UTC 2011 armv7l
Kernel command line: ro elevator=noop vram=32M mem=456M@0x80000000 mem=512M@0xA0000000 root=UUID=998394d0-a519-4e1c-91e3-faef9da1bcdc fixrtc quiet splash console=ttyO2,115200n8
Build Date: 11 August 2011  04:02:01PM
xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.20.2
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct  7 01:51:49 2011
(EE) Unable to locate/open config file: "xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) pvr(0): No drmModeResources available, unable to setup RandR
PVRPreInit: done
PVRScreenInit
PVRScreenInit: done
(EE) AIGLX: reverting to software rendering
(EE) Main Touch Screen: Couldn't open mtdev device
(EE) ioctl EVIOCGNAME failed: Inappropriate ioctl for device
(EE) PreInit returned 8 for "Main Touch Screen"
(EE) Keyboard: Couldn't open mtdev device
(EE) PreInit returned 8 for "Keyboard"


sometimes the XFCE is working, something not...


where is the problem?
what is to do?

(and if its working, i only get a 640x480 solution - not possible to switch in a bigger map)

i have ubuntu omap4 version running on it!

---

### Post by schenkelklopfer on 2011-10-06
important info: its a f***king LG montior (you know the LG Problem with the pandaboard)

---

