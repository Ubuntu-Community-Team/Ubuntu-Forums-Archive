---
title: "twinview problem kde4"
date: 2008-06-30
forum: Desktop Environments
---

### Post by jwferk on 2008-06-30
For the fun of it I have Ubuntu Hardy with Gnome, KDE3.5 and KDE4.1 running on one machine.  I use  a NVIDIA GeForce 8500GT graphics card on an x86_64 setup with the NVIDIA Linux-x86_64-173-14.09 driver and dual monitors.  Things work just fine in Gnome and KD3 under the Twinview setting.  The monitors function as a single screen.

Problem - when I switch to KDE4, the monitors are half Twinview and half separate X-screens.   I can open an application on the primary monitor and drag it to the second just fine.  But, If I try to drag an icon from the primary monitor to the secondary, the icon disappears.   

In Gnome and KDE3, a single wallpaper and panel extends across both monitors.  In KDE4 each monitor requires a separate wallpaper setup.  I can't for the life of me find a setting in KDE4 that allows me to merge the desktops.

The default GUI file is kdm although I have the same problem if I set the default to gdm.

The monitor section of xorg.conf looks like below.  It is the NVIDIA output after running NVIDIA-xconfig and then using the NVIDIA X-server module to configure the monitors to Twinview.

Any suggestions (other than to ask why I have all three desktop environments going on one machine?)

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA902b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

---

### Post by tubasoldier on 2008-06-30
You may want to file a bug report with the KDE developers. It sounds as if that is what it is. Of course I wouldn't be suprized if twinview isn't fully supported in KDE4 as of yet.

[http://bugs.kde.org](http://bugs.kde.org)

---

