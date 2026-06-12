---
title: "3 Monitors 12.0.4 LTS - xrandr shows but screen black"
date: 2014-01-09
forum: Desktop Environments
---

### Post by kschehr on 2014-01-09
Just wanted to post the fix I found for this for my system in case it helps someone out there. I'm running 3 30" 2560x1600 displays off of a ATI 6990 for a resolution of 7680x1600. ATI propriatary drivers (13.12) installed fine, kernel module loaded. After a bit of xorg.conf (below) tweaking I got xrandr to list three monitors at full resolution but one of the three screens would stay blank at boot/start x. 

The "fix" ended up being installing the font packages that /var/log/xorg.0.log. For some reason after installing these font packages all displays began working.


----------- xorg.conf -------------------
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[2]-0"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1600"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP5"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1600"
    Option        "TargetRefresh" "60"
    Option        "Position" "2560 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP9"
    Option        "DPMS" "true"
    Option        "PreferredMode" "2560x1600"
    Option        "TargetRefresh" "60"
    Option        "Position" "5120 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-DFP5" "0-DFP5"
    Option        "Monitor-DFP9" "0-DFP9"
    BusID       "PCI:130:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   7680 2560
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[2]-0"
    Device     "aticonfig-Device[2]-0"
    Monitor    "aticonfig-Monitor[2]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by PopsTheSailor on 2014-01-24
> **kschehr said:**
> 

The "fix" ended up being[COLOR=#ff0000] installing the font packages that /var/log/xorg.0.log. [/COLOR]For some reason after installing these font packages all displays began working.



I'm having some trouble with configuring 2 monitors and found your post.  Installing fonts seems like an odd fix but I'm willing to try. I'm not  understanding what fonts you installed. Are you installing through the  software center or synpatic? If so, can you tell me exactly which  package you installed.

---

