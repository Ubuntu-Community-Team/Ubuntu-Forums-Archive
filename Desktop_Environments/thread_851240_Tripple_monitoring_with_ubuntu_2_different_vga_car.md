---
title: "Tripple monitoring with ubuntu? 2 different vga cards"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Megabug on 2008-07-06
Hi,

I am planning to switch on my main computer from a well knows and hated OS to ubuntu. 

My problem is, that I am using 3 monitors on that PC. In the middle is a 24" TFT and on both sides of it I have 17" TFTs. 

The 24" one is running at the onboard Nvidia 7050PV chipset @ DVI and the both 17"s are running at a Radeon X550 on PCIe x16. 


Oh yes, and the resolutions are:
24" -> 1920x1200
17" -> 1280x1024


So, how can I make things work? As far as I see this, the problem are the different resolutions and/or the different grphic cards?


Thanks in advance...

---

### Post by Megabug on 2008-07-08
Any idea whats wrong? The both screens right and left from my big one are simply dark (not even initialised!)

My config:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "screen1" 0 0
    Screen      1  "screen2" LeftOf "screen1"
    Screen      2  "screen3" RightOf "screen1"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
    Option "Xinerama" "true"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
 # 
    Identifier     "monitor2"
    Gamma           1
EndSection

Section "Monitor"
 # 
    Identifier     "monitor3"
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "vesa"
EndSection

Section "Device"
 # 
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce (fbdev)"
    BusID          "PCI:0:18:0"
    Screen          0
EndSection

Section "Device"
 # 
    Identifier     "device2"
    Driver         "ati"
    VendorName     "ATI"
    BoardName      "ATI Radeon (fglrx)"
    Option         "MergedFB" "off"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Device"
 # 
    Identifier     "device3"
    Driver         "ati"
    VendorName     "ATI"
    BoardName      "ATI Radeon (fglrx)"
    Option         "MergedFB" "off"
    BusID          "PCI:2:0:1"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "800x600"
    EndSubSection
EndSection

Section "Screen"
 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
 # 
    Identifier     "screen2"
    Device         "device2"
    Monitor        "monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
 # 
    Identifier     "screen3"
    Device         "device3"
    Monitor        "monitor3"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024"
    EndSubSection

EndSection

```


Thanks!



Oh yes, and if not Xinerama, what else? randr won't work (shows only one screen, connected to my primary card)

---

### Post by Megabug on 2008-07-27
push...

---

