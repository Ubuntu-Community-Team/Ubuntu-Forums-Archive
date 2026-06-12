---
title: "X will not allow me dualhead(independent)"
date: 2008-12-15
forum: Desktop Environments
---

### Post by schwim on 2008-12-15
Hi there everyone,

I started out trying this on Fedora, but have since tried in Kubuntu.  Both have failed and I can't figure out why.

I've got a brand new install, running nvidia drivers for a 7600 GS card.  Graphics work fine.

I have done it a bunch of different ways, but for instance, using the nvidia-settings applet, I set both monitors to have separate x sessions, save and reboot.  Monitor 0 still works fine, but Monitor 1 shows an X for a cursor over a black screen(unable to create session).  Nothing I try changes that.

If I enable Twinview or xinerama, both monitors work, but twinview is not what I want and xinerama shares a single session(changing desktops on mon 0 changes them on mon 1 as well).  I need two separate sessions.  I've tried looking at my Fedora 7 xorg.conf, as that has it working as I need it, but it doesn't transfer to the updated X properly.

Here's my current xorg.conf:

> 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Proview"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
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


While testing in Fedora, thanks to others' suggestions, [[COLOR="Blue"]I tried a bunch of things[/COLOR]](http://forums.fedoraforum.org/showthread.php?t=207476&highlight=dualhead) to get it working, all to no avail.

I would appreciate any help in getting dualhead up and running again as it's my work rig that I'm trying to update and 3 days to turn a second monitor on makes Jack an unemployed boy.

thanks,
json

---

