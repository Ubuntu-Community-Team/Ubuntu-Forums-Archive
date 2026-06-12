---
title: "Applications starting on wrong screen"
date: 2009-04-23
forum: Desktop Environments
---

### Post by Haise on 2009-04-23
I run three separate monitors on my computer, which necessitates running three separate X servers; that really used to bother me, but I've accepted that a clean multi-monitor setup with 3d acceleration is impossible any other way.

Anyway, since upgrading to 9.04, various applications of the GNOME persuasion (e.g, evolution, gnome-terminal, rythymbox, empathy) will only start on screen 0, which is obviously really problematic.

Does anyone know how to repair this behaviour?

---

### Post by Haise on 2009-04-23
Also, as a side note, each one of my x sessions now features its own persistent cursor, which is something else I'm not a big fan of.

Whenever I sit down, I get to guess which one of the three cursors on my monitors is the actual one.  :P

---

### Post by monkey4ahead on 2009-05-19
Did you find an answer to this problem? I'm having the same issues with a dual monitor setup.

---

### Post by metasparks on 2009-05-25
I'm also looking for help with this.

I have a similar problem asked here: [http://ubuntuforums.org/showthread.php?t=1169637](http://ubuntuforums.org/showthread.php?t=1169637)

> 
I just recently installed Ubuntu 9.04 Jaunty for the first time ever. So far, I've managed to get my three monitors running off my video card (nVidia GTX 295) just fine. However, the problem I have is when I get a notification window from a program sitting in my GNOME Panel 2.26.0, it doesn't go to the monitor which has the panels but to the monitor sitting in the desktop area space most to my left.

I'm running Xinerama. Where can I assign where the notification window (pop-up messages) go to?



Also, is there anything I can do about the mouse cursors left behind when I traverse screens?

---

### Post by FunkyR on 2009-08-14
Has anyone found a sollution for this problem yet? I have the same problem.

nVidia GeForce 6200 GO
Laptop Screen + VGA LCD Screen

xorg.conf:
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 50.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

