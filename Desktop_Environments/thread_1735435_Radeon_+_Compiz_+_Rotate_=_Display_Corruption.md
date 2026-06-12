---
title: "Radeon + Compiz + Rotate = Display Corruption"
date: 2011-04-21
forum: Desktop Environments
---

### Post by jmlsteele on 2011-04-21
Installed Natty a few days ago and everything was working fine.  I have a dual head setup with the left monitor rotated Clockwise 90 degrees (AKA rotate left).  When I setup the the displays properly, instead of just cloning, I noticed a problem, making Unity unusable.  When I apply the rotation either in the xorg.conf fle or using xrandr, the display shows a corrupt looking image.

When I turn compiz off and use metacity instead it works perfectly fine.

Display Adapter:```
01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
```

xorg.conf:```
Section "ServerLayout"
        Identifier      "Desktop"
        Screen          "RightScreen"
        Screen          "LeftScreen" LeftOf "RightScreen"
EndSection

Section "Monitor"
        Identifier      "LeftMonitor"
        Option          "DPMS"          "true"
        Option          "PreferredMode" "1680x1050"
        Option          "TargetRefresh" "60"
        Option          "Position"      "0 0"
        Option          "Rotate"        "left"
EndSection

Section "Monitor"
        Identifier      "RightMonitor"
        Option          "DPMS"          "true"
        Option          "PreferredMode" "1920x1080"
        Option          "TargetRefresh" "60"
        Option          "Position"      "1050 600"
        Option          "Primary"       "true"
EndSection


Section "Device"
        Identifier      "DEV1"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "Monitor-DVI-0" "LeftMonitor"
        Option          "Monitor-DVI-1" "RightMonitor"
EndSection

Section "Screen"
        Identifier      "LeftScreen"
        Device          "DEV1"
        Monitor         "LeftMonitor"
        DefaultDepth    24
EndSection

Section "Screen"
        Identifier      "RightScreen"
        Device          "DEV1"
        Monitor         "RightMonitor"
        DefaultDepth    24
EndSection

Section "Screen"
        Identifier      "Screen"
        Device          "DEV1"
        DefaultDepth    24
        SubSection "Display"
                Virtual 2976 1680 
                Viewport 0 0
        EndSubSection
EndSection

```

---

### Post by MisteR2 on 2011-04-21
I don't have 11.04 right now, but you could try running compiz and metacity side by side. It depends on how your screens are set up, but here's what I went through.

[http://ubuntuforums.org/showthread.php?p=10700873](http://ubuntuforums.org/showthread.php?p=10700873)

---

