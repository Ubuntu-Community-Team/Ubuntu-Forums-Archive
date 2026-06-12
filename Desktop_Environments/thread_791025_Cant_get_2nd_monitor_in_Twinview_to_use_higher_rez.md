---
title: "Cant get 2nd monitor in Twinview to use higher rez then 640x480"
date: 2008-05-11
forum: Desktop Environments
---

### Post by leotemp on 2008-05-11
getting my second monitor to use a higher rez is like pulling teeth from a crocodile. I have the second screen working in twinview but not matter what I do i cannot increase the resolution. I have an Nvidia card so I have setup everything I can in NVIDIA-Settings but the second monitor never has any options aside from 320x240 and 640x480. I have tried to input modes into the Xorg according to the documentation but it isnt very user friendly and all i get is broken desktops.

VIDEO CARD - NVIDIA 8800 GTS 512
Monitor(one that doesnt work) - Gateway FPD1830 (is CRT-1 in nvidia settings)

the following is the contents of my Xorg.conf------------------------------
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1680+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
	Modes      "1024x768"
    EndSubSection
EndSection


Xorg.conf end--------------------------------------

Any ideas about how i can fix this, im going F'ing bonkers here!

---

### Post by chewearn on 2008-05-12
Note the following:
```

HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0

```If you know the actual values required by your monitor (or can find out from the user manual) .  Else, play around with the values, provided you make a back-up xorg.conf first.

I would be inclined to change the HorizSync to something like this first:
```

HorizSync 30.0 - 80.0

```

Be careful not to "over-do" it if you have a CRT monitor (as opposed to LCD); you might cause real damage.

---

