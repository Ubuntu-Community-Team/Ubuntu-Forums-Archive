---
title: "Dual Monitor Problem: ATi Radeon HD 3870"
date: 2009-06-22
forum: General Help
---

### Post by The-Don on 2009-06-22
Howdy,
I've used the 'Search Function' but haven't found the solution to this particular problem.

_**Current Situation**_

[LIST]
[*]The monitor on my right is the one I want to be able to use as primary.
[*]The monitor on my left is the one I want to be able to use as secondary.
[*]The monitor on my left is what I'm writing in right now, I can't even move the mouse to the monitor on the right. I'm locked in this single window with no way to go to the other display.
[/LIST]
_**Ideal Situation**_

[LIST]
[*]Monitor on my right as the master/primary baby.
[*]The ability to move things over to the 'Left' screen.
[/LIST]
[B]_Specs_
O/S:[/B] Ubuntu 9.04 (32-bit)
**GPU:** ATi Radeon HD 3870 (Dual Head)
** Driver Installed:** ATi Catalyst 9.6
** Monitor Left:** Packard Bell 900W (19")
** Monitor Right:** Acer 2016W (21")
** Resolutions on Both:** 1440x900

P.S.
Whenever I attempt to swap the displays around and set resolution rates in CCC, the program goes grey, freezes, takes a couple of minutes to exit. And then forgets all the settings :\ and whenever I play with the xorg.conf file, I always have to call up my current working one.

```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 1680 0
    Screen         "aticonfig-Screen[0]-1" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    SubSection "Display"
        Virtual   2880 900
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1440x900"
    EndSubSection
EndSection

```Thanks in advance.

---

### Post by oliwek on 2009-10-10
for people interested : if you use proprietary drivers (catalyst/fglrx for Ati cards), when you manually edit /etc/X11/xorg.conf

you then have to type in terminal : 

```
sudo aticonfig --input=/etc/X11/xorg.conf
```

then reboot (or restart gdm) to test

don't forget to backup xorg.conf first

---

