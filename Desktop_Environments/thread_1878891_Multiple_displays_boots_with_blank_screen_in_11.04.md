---
title: "Multiple displays boots with blank screen in 11.04 and 11.10.  My xorg.conf right?"
date: 2011-11-10
forum: Desktop Environments
---

### Post by DJS2 on 2011-11-10
My current setup is 1 monitor and 4 ati radeon hd 6970 cards (for multi gpu tools).  I am currently using ATI Catalyst 11.4 drivers and Ubuntu 11.04.

When I start my computer I get bios and everything but after Ubuntu boots I get a blank screen (with signal to monitor).  

My xorg.conf file:
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
    Screen         "aticonfig-Screen[2]-0" RightOf "aticonfig-Screen[1]-0"
    Screen         "aticonfig-Screen[3]-0" RightOf "aticonfig-Screen[2]-0"
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
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[2]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[3]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:3:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:4:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[2]-0"
    Driver      "fglrx"
    BusID       "PCI:5:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[3]-0"
    Driver      "fglrx"
    BusID       "PCI:6:0:0"
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

Section "Screen"
    Identifier "aticonfig-Screen[3]-0"
    Device     "aticonfig-Device[3]-0"
    Monitor    "aticonfig-Monitor[3]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Does anyone have an idea on what my problem could be?  Any help would be appreciated, thanks!

---

### Post by NeTRaW on 2012-02-04
Hi mate, i've the same problem, after activating all the gpus (aticonfig --initial --adapter=all), and reboot, I can see only blank screen, but monitor have signal. Did you solved it?

Best Regards,

---

### Post by HughJarse on 2012-02-04
ubuntu is poor with multiple screens.
I have 2 screens working perfectly in 10.04.
After upgrade to 11.10 can't even detect the second screen.
Running O/S from the CD it was fine.:confused:
Annoying as that was the main thing I was testing.

---

