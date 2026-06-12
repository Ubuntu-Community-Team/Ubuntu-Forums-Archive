---
title: "Monitor not detected - 640x480 at startup"
date: 2010-07-11
forum: Desktop Environments
---

### Post by ^_Pepe_^ on 2010-07-11
Hi all,

My Ubuntu server box, has a Iiyama prolite LCD, 22", 1680x1050, that had not problem at all since... I can remember.

But..

Since yesterday, after a restart, xserver started in 640x480, with only 320x240 as alternative.

I have latest nVidia drivers installed, and the main difference with last week, is that now, Display Configuration says CRT-1, unknown instead of Iiyama.

I've tried.

1. Uninstall xserver and reinstall. 
2. dpkg reconfigure
3. Uninstall nVidia and come back to original Nouveau.

No luck.

Things that I've guessed:

1. If I plug my gaming monitor (Iiyama 26" 1900x1200 through DVI-DVI), there's not problem at all. Now I'm currently using a VGA-VGA cable with a DVI-VGA adapter in the nVidia 9500 output.

2. My old Ubuntu 9.10 configuration (still in GRUB) doesn't work either!! So that's why I think this can be a hardware problem.

3. If I use only the DVI-DVI cable and the 22" monitor, nVidia drivers detect Iiyama, all resolutions...I can change to 1680x1050...but after a restart, again goes to 640x480 and I have to manually change.

I've modified manually my xorg.conf in this way

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

# HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       31.0 - 90.0
    VertRefresh     60.0
    ModeLine       "1680x1050_60" 147.140 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

and now I can even use the VGA-VGA cable, but after a restart, 640x480 appear again.

In the logs I can find this information about EDID

```
pepe@HOMER:/var/log$ cat Xorg.0.log | grep -E "(WW)|(EE)" | grep -v unknown
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loading extension MIT-SCREEN-SAVER
(WW) Jul 11 17:59:34 NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
(WW) Jul 11 17:59:34 NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) Jul 11 17:59:34 NVIDIA(0):     from CRT-1's EDID.

```

Any help would be appreciated

Thanks in advance.
^_Pepe_^

---

### Post by pietjanjaap on 2010-07-11
gnome-display-properties
Start this with "gksudo gnome-display-properties" in the terminal.
There was something with not able to save the file.

[http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)

---

### Post by ^_Pepe_^ on 2010-07-11
Hi.

Thanks for your comments.

I finally could write in xorg.conf through sudo gedit ... and with the command you posted.

So, this is not the problem, but your comment give an idea!:

What if I create a new user in my box?

I've created a new user and it worked, even with restart. If I use my old user, it still start with 640x480.

Weird, but at least I have a workaround, and I don't have to buy a DVI-DVI 

Thanks. 

Anyway I'd like to know what has happened to my old user.

^_Pepe_^

---

