---
title: "compiz installed;now what?"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by Xoanan on 2007-10-05
Hi All 

I have compiz now on Xubuntu now(not sure how) but its there.  I have attempted to configure it and enable it, but, nothing seems to happen.  Everytime, I go back to Settings- . GL Desktop, it is always disabled,  

I am running with an i810e(although the GL Menu says its an 82810e)  

What am I missing?

Thanx all

Xoanan:popcorn:

---

### Post by Xoanan on 2007-10-05
Here&#347; more sysinfo

Graphics card/monitor

Section "Device"
        Identifier      "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Driver          "i810"
        BusID           "PCI:0:1:0"
EndSection

Section "Monitor"
        Identifier      "DELL M570"
        Option          "DPMS"
EndSection

Xubuntu Release info
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
i686

OpenGL
direct rendering: No
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:

AIGLX (intel)
/var/log/Xorg.0.log:(==) AIGLX enabled
/var/log/Xorg.0.log:(EE) AIGLX: Screen 0 is not DRI capable
/var/log/Xorg.20.log:(==) AIGLX enabled
/var/log/Xorg.20.log:(EE) AIGLX: Screen 0 is not DRI capable
/var/log/Xorg.21.log:(==) AIGLX enabled
/var/log/Xorg.21.log:(EE) AIGLX: Screen 0 is not DRI capable

Compiz Version

ii  compiz                                0.3.6-0gandalfn11                    OpenGL composition manager - transitional pa
ii  compiz-core                           0.3.6-0gandalfn11                    OpenGL composition manager - core binaries e
ii  compiz-extra                          0.3.6.0-0gandalfn3                   Community contribution to compiz
ii  compiz-extra-gnome                    0.3.6.0-0gandalfn3                   Community compiz plugins gnome schemas
ii  compiz-extra-plugins                  0.3.6.0-0gandalfn3                   Community compiz plugins
ii  compiz-gnome                          0.3.6-0gandalfn11                    Gnome window decorator and libraries for Com
ii  compiz-plugins                        0.3.6-0gandalfn11                    Gnome window decorator and libraries for Com
ii  gnome-compiz-manager                  0.10.2-0gandalfn4                    Compiz Gnome Manager
ii  libgnome-compiz-manager               0.10.2-0gandalfn4                    Compiz Gnome Manager


Incidentally, when I relaunch the OS, the only options I have for sessions is last session, xfce session, default session, failsafe gnome and failsafe terminal.  

I must bee missing something here.

---

