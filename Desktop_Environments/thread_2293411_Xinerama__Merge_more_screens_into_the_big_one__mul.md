---
title: "Xinerama / Merge more screens into the big one / multigpu multihead setup"
date: 2015-09-04
forum: Desktop Environments
---

### Post by ladkoma on 2015-09-04
Hi guys, 
I apologize for bothering you like that, but after ages of hassling around the xorg.conf I decided to ask over here.

I am building kind of video wall set up 2x2 at this moment and I am trying to figure out how to "merge" X screens into the big one. Just like AMD Eyefinity of nVidia Mosaic does that.
And all this is just because I would like to run fullscreen apps spanned across more screens/monitors. (eg. web browser, movie player)

[ftp://www.x.org/pub/X11R6.8.2/doc/xorg.conf.5.html](ftp://www.x.org/pub/X11R6.8.2/doc/xorg.conf.5.html) - Xorf.conf manpage actually did not help as this scenario has not been mentioned in there.

Is that possible somehow? I tried a lot and usually ended up recovering the last working xorg.conf



The plan is to create "profiles" for video, web, others and switch between them using shortcuts.
Thanks a lot!
Lad

EDIT:
Working pre-generated xorg.conf made by ATI drivers
Just if it could merge these four screens into the big one

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 1920 1200
    Screen      1  "amdcccle-Screen[1]-1" 0 1200
    Screen      2  "amdcccle-Screen[5]-0" 1920 0
    Screen      3  "amdcccle-Screen[5]-1" 0 0
    Option      "Xinerama" "true"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-DFP3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[5]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "1-DFP1"
    BusID       "PCI:5:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[5]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "1-DFP3"
    BusID       "PCI:5:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP3" "0-DFP3"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[5]-0"
    Device     "amdcccle-Device[5]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[5]-1"
    Device     "amdcccle-Device[5]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-1"
    Device     "amdcccle-Device[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

