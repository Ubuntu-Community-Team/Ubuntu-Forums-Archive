---
title: "Help setting up 3-monitor xorg.conf file"
date: 2009-06-16
forum: Desktop Environments
---

### Post by pomegrante on 2009-06-16
Hello everyone.  I am trying to setup my xorg.conf file and am in need of assistance!

I have a Dell Latitude D620 with an Intel Graphics Media Accelerator 950 connected to a docking station, totaling 3 monitors:  The laptop screen, and then 2 19" Dell LCDs.

I would like to have the two Dell LCDs share an X screen (for a combined resolution of 2560x2048, and then have a separate X screen on the laptop monitor.  If this is not possible, I would be happy with a separate X screen on each monitor.

This is what my xorg.conf file looks like so far:
```

Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
        Screen  0       "laptop"
    Screen    1    "lcd1"
    Screen     2    "lcd2"
        Option  "Xinerama"      "true"
EndSection

Section "Monitor"
    Identifier    "laptop"
    Option    "PreferredMode"    "1440x900"
EndSection

Section "Monitor"
    Identifier    "lcd1"
    Option    "PreferredMode"    "1280x1024"
EndSection

Section "Monitor"
    Identifier     "lcd2"
    Option "PreferredMode" "1280x1024"
EndSection

Section "Screen"
    Identifier    "laptop"
    Monitor        "laptop"
    Device        "Card0"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "lcd1"
    Monitor        "lcd1"
    Device        "Card0"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection


Section "Screen"
    Identifier    "lcd2"
    Monitor        "lcd2"
    Device        "Card0"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection


Section "Device"
    Identifier    "Card0"
    Driver        "intel"
    BusID        "PCI:0:2:0"
    Option    "monitor-LVDS" "laptop"
    Option    "monitor-TMDS-1" "lcd2"
    Option    "monitor-VGA" "lcd1"
EndSection

```I imagine that my errors are many, as I have been building my file based on various resources.  Let me know if anything else is needed.  Thanks!

---

