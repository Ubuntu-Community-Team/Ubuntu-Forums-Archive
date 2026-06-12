---
title: "Xorg.conf : Setting a custom resolution"
date: 2011-05-18
forum: Desktop Environments
---

### Post by paddy.melon on 2011-05-18
So, I've been playing a lot lately and somehow stuffed my drivers, etc., etc. I didn't have a backup of my xorg.conf so I've had to generate a new one. This is all fine. Only, for some reason, my old Samsung Monitor (CRT-0) won't give an EDID (I swear it did before). Thus, it's setup as 640x480 by default. Naturally, this is really, really annoying and almost unusable as a secondary display to a 1366x786 Viewsonic (the CRT-1).

So, I've stuffed around for the past day or so with no luck. I've tried various ModeLines but I haven't done much of this before so I'm probably doing something wrong. Here's my xorg.conf so far. Everything is setup exactly how I like it except the resolution of the CRT-0:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    ModelName      "CRT-0"
 #   Modeline       "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
#    Option        "UseEDID" "FALSE"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 240"
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "1280x1024 1366x768"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "TwinView" "1"
#    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +1366+288, CRT-1: 1366x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Thanks for any help!

---

### Post by truck87bp on 2011-05-18
I found this on the web but have no idea how to make it work. I have also had dual monitor problems and have been fighting it for 5 days now.

[http://nxadm.wordpress.com/2011/05/13/define-the-main-screen-in-ubuntu-unity-dual-screen-setup/](http://nxadm.wordpress.com/2011/05/13/define-the-main-screen-in-ubuntu-unity-dual-screen-setup/) 

Maybe you can figure it out. Good Luck.

---

### Post by paddy.melon on 2011-05-19
> **truck87bp said:**
> I found this on the web but have no idea how to make it work. I have also had dual monitor problems and have been fighting it for 5 days now.

[http://nxadm.wordpress.com/2011/05/13/define-the-main-screen-in-ubuntu-unity-dual-screen-setup/](http://nxadm.wordpress.com/2011/05/13/define-the-main-screen-in-ubuntu-unity-dual-screen-setup/) 

Maybe you can figure it out. Good Luck.

THanks but the problem isn't really in dual monitors... got that all sorted out fine. The issue is in the incorrect resolution as the result of a missing EDID. Am I able to force my own EDID? If so, how would I make a 1024x768, etc.?

---

