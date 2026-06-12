---
title: "Nvidia X Settings and xorg.conf"
date: 2009-07-24
forum: Desktop Environments
---

### Post by roypk on 2009-07-24
Hi,

First of all, I'm a linux noob so please, don't expect me to already know the simple stuff.  I'm running the 64-bit 9.04 and have been having some problems setting up the screens.  My VGA card is a 9600GT and I use dual screens.  The Nvidia Xserver Settings doesn't appear to be capable of writing to the xorg.conf file so I copied and pasted the stuff to the file myself.  I also deleted some of the old configs in the file.  Although, everything seems to be working.  I don't know whether I've done anything wrong or not.  Here is what's in the xorg.conf.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
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
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2343"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1024x768_60 +0+0, DFP-1: 1024x768_60 +1024+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Could someone, please, take a look at it and tell me whether anything is missing or not.  Just a few more question.  If I want to change the resolution, which part(s) do I have to edit?  Is there anything I could do to get the Nvidia X Setting working?

Best regards,
Roy

---

### Post by kpkeerthi on 2009-07-24
Enter this command from a terminal window
```
gksudo nvidia-settings
```
and it should be able to write to xorg.conf

---

### Post by roypk on 2009-07-24
> **kpkeerthi said:**
> Enter this command from a terminal window
```
gksudo nvidia-settings
```
and it should be able to write to xorg.conf

Thank you.

Best regards,
Roy

---

### Post by SuperSonic4 on 2009-07-24
> **kpkeerthi said:**
> Enter this command from a terminal window
```
gksudo nvidia-settings
```
and it should be able to write to xorg.conf

This is the correct command but to expand using gksudo runs the nvidia-settings app with root powers so you can now save to /etc/X11

---

