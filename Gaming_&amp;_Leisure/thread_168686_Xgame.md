---
title: "Xgame"
date: 2006-05-01
forum: Gaming &amp; Leisure
---

### Post by Megatog615 on 2006-05-01
I get the following error after running sudo xgame-gtk2, and then running either update-manager or synaptic:
```
Failed to run /usr/bin/update-manager

Unable to copy the user's Xauthorization file.
```
If I don't run xgame-gtk2 with sudo, I get "Unable to lock authorization file".

What is the proper way to install xgame-gtk2?

---

### Post by frodon on 2006-05-02
workaround here : [http://ubuntuforums.org/showpost.php?p=781066&postcount=13](http://ubuntuforums.org/showpost.php?p=781066&postcount=13)

---

### Post by Megatog615 on 2006-05-06
I get this error when running games:
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux falcon-2 2.6.15-21-386 #1 PREEMPT Fri Apr 21 16:43:33 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.94.log", Time: Sat May  6 15:08:29 2006
(EE) Unable to locate/open config file: "xorg.conf-game"

xf86AutoConfig: Primary PCI is 5:0:0
Running "getconfig -X 70000000 -I /etc/X11,/usr/etc/X11,/usr/lib/xorg/modules,/usr/lib/X11/getconfig -v 0x10de -d 0x0092 -r 0xa1 -s 0x3842 -b 0xc518 -c 0x0300"
sh: getconfig: command not found
(==) Using default built-in configuration (43 lines)

Fatal server error:
Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":94.0"
      after 0 requests (0 known processed) with 0 events remaining.
```
Something with getconfig?

Oh, and I still get the same Xauthority error.

---

### Post by Megatog615 on 2006-05-10
*bump*

---

