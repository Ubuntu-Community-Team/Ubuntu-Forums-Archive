---
title: "Xorg.conf thinks display is twice as big as it actually is"
date: 2009-05-26
forum: Desktop Environments
---

### Post by pkkid on 2009-05-26
I am having an issue trying to get my desktop to use the correct display.  I have a dell 1280x1024 monitor and an NEC 1680x1050 monitor (using an ATI graphics card) for a total of 2960x1050.  However, Gnome keeps thinking its a size twice this and stretches my wallpaper accordingly creating the ugliest of backgrounds.  My xorg.conf is below. (NOTE: If I take out the 'Virtual' line, Gnome draws both displays as 1280x1024 which is semi right, except the larger monitor is at the wrong resolution.

```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier  "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "EnableRandR12" "false"
        Option      "DesktopSetup" "horizontal"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier  "aticonfig-Screen[0]-0"
        Device      "aticonfig-Device[0]-0"
        Monitor     "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Modes     "2960x1050"
                Virtual   2960 1050
                Viewport  0 0
                Depth     24
        EndSubSection
EndSection

```

---

