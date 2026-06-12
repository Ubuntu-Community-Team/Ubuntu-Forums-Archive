---
title: "Dual monitor not working as I want it"
date: 2009-12-11
forum: Desktop Environments
---

### Post by B3rt on 2009-12-11
I use Ubuntu 9.10 and connected a second monitor.
The monitor works but I cannot get it to run as I want it.

My setup:
- ubuntu 9.10
- nvidia G98 (GeForce 8400 GS)
- driver used "nivdia"
- using compiz
- right (primairy) monitor Toshiba PA3553 (22") @1680x1050
- left (secondary( monitor Samsung Syncmaster 940w @1440x900

What I want to achieve is that both monitors act as separate desktops, this means when I maximize a windows it maximizes to only the monitor on which it is on. Also it should be possible to move windows from 1 to the other monitor.

I now works when I maximize it stays on 1 monitor but I cannot move screens/windows between the 2 monitors.

Can please someone help me configuring this?

This is my current xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1440 0
    Screen      1  "Screen1" LeftOf "Screen0"
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
    ModelName      "Toshiba PA3553"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: 1680x1050 +0+0, CRT-1: nvidia-auto-select +0+0; CRT-0: 1680x1050 +0+0, CRT-1: nvidia-auto-select +240+75"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
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
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by B3rt on 2009-12-16
The problem is that I must use twinview on 2 different size monitors, this seems not to be working as in Windows.

Has no one an idea how to fix this?

---

### Post by Grenage on 2009-12-16
I had the same card with the same TV :)

Basically, you'll want to use twinview.  To have the screens be separate desktops you would be running separate X instances, so you can't drag windows across.  What issues is twinview giving you?

---

### Post by B3rt on 2009-12-16
the 2 monitors are of different sizes, 
The desktops sizes to the larges monitor, this results that on the smallest monitor I miss a complete section at the bottom size of the screen.

twinview only works fine if you have 2 identical sizes monitors.

On windows this is no problem at all.....

---

### Post by Grenage on 2009-12-16
I use twinview with different monitor sizes!

---

### Post by ean5533 on 2009-12-16
> **B3rt said:**
> the 2 monitors are of different sizes, 
The desktops sizes to the larges monitor, this results that on the smallest monitor I miss a complete section at the bottom size of the screen.

twinview only works fine if you have 2 identical sizes monitors.

On windows this is no problem at all.....

I'm betting that your smaller monitor does not support the resolution that you're setting. For example, maybe your big monitor support 1600x1200, but your smaller monitor only support 800x600. Try turning the resolution down a notch and see if that helps.

---

### Post by egravede on 2009-12-16
Try making the window your in smaller before moving it over to the other screen.  Like what ean said, your other monitor probably isn't able to support the size and thus isn't letting you drag the window across.

---

### Post by B3rt on 2009-12-16
No this is not the problem.
Both monitors are of the latest generations.
1 monitor supports 1680x1050 the other one 1440x900 (both wide screen)

The problem is that if I maximize on the smaller one i miss about 50mm on top the window, here is normally the taskbar, this one is missing
At the bottom size the screen maximizes so far I miss the bottom part of my window which i maxized.

---

### Post by Grenage on 2009-12-17
To be honest I am not sure what you mean, but possibly overscan?  Have you got any pics?

---

