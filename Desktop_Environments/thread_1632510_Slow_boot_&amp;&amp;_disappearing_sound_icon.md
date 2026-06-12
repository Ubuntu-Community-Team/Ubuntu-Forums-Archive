---
title: "Slow boot &amp;&amp; disappearing sound icon"
date: 2010-11-28
forum: Desktop Environments
---

### Post by mariost on 2010-11-28
I have switched from gnome to xfce for its speed  and customization ability. But from some time on I experience 35 second  wait for xfce to boot. Even gnome boots faster! Its not caused by  startup programs, and I believe this is not /etc/X11/xorg.conf issue either, despite that ill post its contents:
```
[INDENT]Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
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
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "TargetRefresh" "75"
    Option        "Position" "1366 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
    Option        "PreferredMode" "1280x1024"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2646 2646
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
[/INDENT]
```[INDENT]

The other problem is having no sound icon for xfce4-mixer loaded in the xfce4-panel when i start up xfce after a shutdown/restart. If I execute
```
killall xfce4-panel; sleep 3; xfce4-panel&
``` the icon is up and running. It shows up too if I stop service gdm, then "sudo service gdm start". I tried running the script for kill/respawn i mentioned above at startup, but it doesnt work, unless entered manually. That should be some easy to fix problem, but i know not of the fix...
Ubuntu Maverick (10.10) 2.6.35-22-generic-pae
[/INDENT]

---

