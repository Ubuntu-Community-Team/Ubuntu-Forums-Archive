---
title: "Resolution resets to default on startup"
date: 2009-09-22
forum: Desktop Environments
---

### Post by jmc200 on 2009-09-22
Hi,

I've got an m9765uk PC from HP - it's 64-bit and contains a GT220 graphics card. On booting ubuntu 9.04 for the first time, the resolution was rubbish and the graphics card was clearly not being used. I had to go get a proprietary driver (from [ftp://download.nvidia.com/XFree86/Linux-x86_64/190.32/](ftp://download.nvidia.com/XFree86/Linux-x86_64/190.32/)) to make use of my card, and all is now good, except... When I start up, the resolution resets back to the pre-driver state, and all of my icons have moved about. The login screen appears to be at the correct resolution, but for some reason the resolution changes while the screen is black after entering my password (you can see the cursor change size).

I used "gksudo nvidia-settings" to set the correct resolution, 1920x1080, and save this config to Xorg.conf, but this has no effect. Any ideas, please? This is obviously not the end of the world but is a bit annoying, and moreover it is fast becoming ammunition for my anti-linux friends! ;)


Xorg.conf:
-----
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    #  Modes       "1920x1080"                (tried adding this but to no effect)
    EndSubSection
EndSection

---

### Post by tgeer43 on 2009-09-22
I don't know if this is the answer to your problem but from what I've read, the 190.32 driver is quirky at best. The 190.62 driver *may* give you better results. It's not available yet for regular download from Nvidia's website but it's floating around out there somewhere. You'll just have to look a bit.

That is an unusual problem though, resetting like that. Have you tried any other resolutions and/or refresh rates yet to see if they 'stick'?

tgeer

---

### Post by jmc200 on 2009-09-24
Hey,

Thanks for your response. I've tried fiddling with resolution & refresh rate, but no joy.

Bizarrely, I sometimes find that right-click menus behave as if the resolution is still small (e.g. if I right-click at the bottom right of the screen, the menu appears halfway between the top-left and bottom-right corners). Dodgy drivers would presumably explain it, so I will hunt for the 190.62 driver as you suggest...

---

