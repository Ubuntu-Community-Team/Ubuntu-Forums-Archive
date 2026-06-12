---
title: "kde 4 dual monitor ATI X1300"
date: 2008-12-22
forum: Desktop Environments
---

### Post by magickangaroo on 2008-12-22
Hi all

I was hoping for some help with a dual display issue for ibex.

I am running kde4.1.  I can drag a window over the second monitor, however if i try to split it across it will crash X11 back to kdm.  i can move my mouse in the second screen with no issues, but it dosn't display a desktop, nor any widgets etc.

I'm pretty sure this is to do with kde rather than X11. But any advice would of course be appreciated.

thanks

/Mgk

Details as below

I configured aticonfig with
```
 aticonfig --initial --dtop=horizontal
```

X11 and fglrx info

```
adz@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.1.8087 Release

adz@ubuntu:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load    "dbe"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by magickangaroo on 2008-12-23
If there is extra info needed, please say. Or if this is covered else where please let me know, i have looked at threads with Kde4 ati and dual in the title.

Thanks

---

