---
title: "(3) monitors (2) video cards xorg.conf help!"
date: 2012-01-29
forum: Desktop Environments
---

### Post by dknise on 2012-01-29
Hey guys,

So clearly, I am brand new to Ubuntu and I am trying to set up my monitors with the xorg.conf settings.  When I edit and reboot, it fails to load the login screen.  I then boot into the console and remove the file and then restart and it boots properly, with no xorg.conf to refer to.

When it boots without a xorg.conf, both of the screens attached to the PCI 1:0:0 get displayed, but not the one on the PCI 2:0:0 slot.

```

Section "ServerLayout"
    Identifier     "threescreens"
    Screen       0 "screen_left" 0 0
    Screen         1 "screen_center" RightOf "screen_left"
    Screen       2 "screen_right" RightOf "screen_center" 0 0
    Option           "Twinview" "on"
    Option           "Xinerama" "on"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "asus_left"
    VendorName   "ASUS"
    ModelName    "VE247"
    HorzSync     30.0 - 83.0
    VertRefresh  50.0 - 76.0
    Option         "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "asus_center"
    VendorName   "ASUS"
    ModelName    "VE247"
    HorzSync     30.0 - 83.0
    VertRefresh  50.0 - 76.0
    Option         "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "asus_right"
    VendorName   "ASUS"
    ModelName    "VE247"
    HorzSync     30.0 - 83.0
    VertRefresh  50.0 - 76.0
    Option         "DPMS" "true"
EndSection

Section "Device"
    Identifier   "graphicscard_top1"
    Driver       "fglrx"
    BusID        "PCI:1:0:0"
    Screen         0
EndSection

Section "Device"
    Identifier   "graphicscard_top2"
    Driver       "fglrx"
    BusID        "PCI:1:0:0"
    Screen         1
EndSection

Section "Device"
    Identifier   "graphicscard_bottom"
    Driver       "fglrx"
    BusID        "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier   "screen_left"
    Device       "graphicscard_top1"
    Monitor      "asus_left"
    DefaultDepth     24
    Option       "TwinView" "0"
    SubSection "Display"
        Depth  24
        Modes  "1920x1080"
    EndSubSection
EndSection

Section "Screen"
    Identifier   "screen_center"
    Device       "graphicscard_top2"
    Monitor      "asus_center"
    DefaultDepth     24
    Option       "TwinView" "0"
    SubSection "Display"
        Depth  24
        Modes  "1920x1080"
    EndSubSection
EndSection

Section "Screen"
    Identifier   "screen_right"
    Device       "graphicscard_bottom"
    Monitor      "asus_right"
    DefaultDepth     24
    SubSection "Display"
        Depth  24
        Modes  "1920x1080"
    EndSubSection
EndSection




```I think I've read every post about this ever made on the internet and have spent hours trying to get it to work!!! ahhhh haha.  So any help for a complete newb would be awesome.:D

Thanks.=)

---

### Post by dknise on 2012-01-29
BUMP cause I really need some help on this!!

---

### Post by kragebein on 2012-01-29
Hi.
I belive "Twinview" is a nvidia setting, you might try to use "BigDesktop" which is (or atleast used to be) a flgrx setting.

for nvidia, we have 'nvidia-settings' we can run, there should be something similar for your graphic card too =)

---

