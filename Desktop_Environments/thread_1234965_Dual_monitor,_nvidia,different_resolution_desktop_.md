---
title: "Dual monitor, nvidia,different resolution desktop size problem"
date: 2009-08-08
forum: Desktop Environments
---

### Post by essarf on 2009-08-08
Hi. I'm running a Ubuntu Jauty desktop system with Gnome.

I have two monitors, one widescreen 22"(1440x900) and one 17" 4:3 (1280x1024). They are set up with twinview using the nvidia-settings driver.

Now, here is the problem/issue: The total desktop screen will be about 2720x1024. That will make the desktop go out of the primary 22" monitor. For instance, when I move the mouse cursor down, it'll end up out of the screen. 

All panels are showing correct though, so it's a minor problem. However, I thought there might be a solution to this, since it all works just fine when I have this setup in Windows Vista.


Thanks for any assistance.

---

### Post by unf on 2009-08-08
> 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Monitor"

    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VP171b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

I have 2x17". nvidia-settings sorts them like this. 

See what you have in "/etc/X11/xorg.conf"

This it not relevant: I have a different problem with 2 GPU 3 Displays 2x17"LCD + 40" LCDTV

---

### Post by amites on 2009-12-05
Similar issue, I just added a
Viewsonic 22" Widescreen (nx2232w) which lists it's optimal resolution at 1600x1050

it is sitting next to a 17" that won't go above 1280x1024

I originally hacked at my xorg.conf file to get the 17" to play nicely with another at the same resolution, and have both running at 1280x1024 rather easily

however I'm running into frustration with getting the 22" to display larger - has anyone figured out a solution for this?

my plan of attack so far has been to enter custom modeline's though I've been unable to generate one in the range for this monitor

the vsync range is 60-75hz when I generate a modeline for this with 1600x1050 the lowest hsync range I've seen is 64khz
which is above the 60khz limit it is set for

when I run ddprobe it says it wants to run at 1600x1050@77

so far all attempts have led to one issue or another, primarily a blue screen that says no signal and the display on only the 17"

any thoughts are appreciated, my xorg.conf is pasted below for general reference - includes a few extra lines from things I've tried


```
Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Viewsonic"
    ModelName      "CRT-0"
    HorizSync       64.0 - 64.0
    VertRefresh     69.0
#    ModeLine       "1680x1050@69" 139.00 1280 1312 1840 1872 1024 1044 1056 1076
#	Modeline       "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
#	Modeline "1680x1050@75" 210.42 1680 1712 2504 2536 1050 1070 1083 1103
	Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Gateway"
    ModelName      "CRT-1"
    HorizSync       64.0 - 64.0
    VertRefresh     60.0
    ModeLine       "1280x1024@69" 139.00 1280 1312 1840 1872 1024 1044 1056 1076
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 A-LE"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
#    Option         "metamodes" "CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0"
#    Option         "metamodes" "CRT-0: 1680x800 +0+0, CRT-1: 1280x1024 +1680+0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    Option         "UseEdidDpi" "FALSE"
    Option         "UseEdid" "FALSE"
    Option         "DPI" "96 x 96"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

