---
title: "desktop cloned from Notebook into TV LCD"
date: 2010-05-03
forum: Desktop Environments
---

### Post by karolosz on 2010-05-03
Hello I'm using Ubuntu 9.10 with the 
 toshiba A300 1EG, Radeon ATI hd3470 with the drivers ATI, 
my  TV is LCD samsung 40"
connection TV & notebook by wire VGA


IT was worked properly about one month ago, i cannot tell what could change...
righte now i cannot clone my desktop from notebook into LCD TV

computer recognized my TV properly, but it doesn't worked i see just black screen;

I trie to use: SYSTEM-> preference-> screen -? clone the screen- but no effects;
I also tried by ATI Catalyst control centre Administrative-> screen management- no effect (screen recognized properly.. but it doesn't helped)

 when i go to xorg by
 "sudo gedit /etc/X11/xorg.conf"

i found:
```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "&#344;>ÜHRýHRý" "true"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "0v    hy    fresh" "true"
    Option        "H&#269;§    *r" "true"
    Option        "PreferredMode" "1280x800"
    Option        "TargetRefresh" "60"
EndSection

Section "Monitor"
    Identifier   "0-LCD"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x800"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LCD" "0-LCD"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
    SubSection "Display"
        Virtual   2063 1600
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2063 1600
        Depth     24
    EndSubSection
EndSection
```

there is some werid marks like: [img]http://img219.imageshack.us/img219/4684/zrzutekranul.jpg[/img] - is it just a displaying??

HOW could i clone my desktop back again????

---

### Post by karolosz on 2010-05-06
no solutions, nobody knows ???

---

