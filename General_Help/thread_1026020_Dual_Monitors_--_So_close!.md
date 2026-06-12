---
title: "Dual Monitors -- So close!"
date: 2008-12-30
forum: General Help
---

### Post by qazwart on 2008-12-30
I have a Dell Optiplex with ATI graphics card and two Dell monitors. I've been trying to get dual monitors configured, and I am so close. I have two desktops, I can drag a mouse between the two desktops, but I cannot drag a window between the two desktops.

I've tried the aticonfig --overlay-on=1 and aticonfig --overlay-on=0, but neither one seems able to get me one big desktop.

Here's the output of my xorg.conf file:

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "Default Screen" 0 0
        Screen         "aticonfig-Screen[0]-1" LeftOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "0"
        Option      "SwapScreens" "on"
        Option      "ScreenOverlap" "30"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"

EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


I'll try a few other things for now. If anyone has any ideas, please let me know.

---

### Post by Woody1987 on 2008-12-30
Xinerama is what i belive you need. You could also try the opensource Radeon driver which i think has support for xrandr1.2 which can also work.

---

### Post by deathsshadow77 on 2008-12-30
I cant be much help in terms of xorg but I will say that once I checked pre-released updates and unsupported updates in the updates tab of software sources I was able to get dual screens working nicely through the catalyst. 
I dont recommend this since it might ruin your install or something but I did it and dual monitors work now.

---

### Post by linux_tech on 2008-12-30
Try adding -

Section "ServerFlags"
Option "Xinerama" "true"
EndSection

before the Section "ServerLayout"

refer to this post-
[http://ubuntuforums.org/showthread.php?t=289967](http://ubuntuforums.org/showthread.php?t=289967)

---

### Post by Burmuda on 2008-12-30
If you don't need 3D stuff use the "radeon" drivers and xrandr. Otherwise:
I use this xorg.conf for my ati card:
```
Section "Files"
EndSection

Section "Module"
        Load  "glx"
        Load  "dri"
EndSection

Section "ServerFlags"
        Option      "AllowMouseOpenFail" "on"
        Option      "IgnoreABI" "on"
        Option      "AIGLX" "true"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   2704 1050
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option      "DAMAGE" "true"
        Option      "Composite" "true"
EndSection

```

I think especially the SubSection "Display" with the Virtual (combined) resolution for your monitors is important (in my case 1680 + 1024 width and 1050 hight).

Using this xorg.conf I selected "big desktop" in amdcccle (ccc == Catalyst Control Center?) and got one spanned desktop over two monitors.

---

