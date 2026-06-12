---
title: "Monitor settings not saved"
date: 2008-11-29
forum: Desktop Environments
---

### Post by Hydrohs on 2008-11-29
I have two monitors set up, I configure them with NVIDIA X Server Settings and everything is good (I'm running them with TwinView) until I log off or restart. Then my second monitor gets disabled, and I have to manually re-apply the settings every time. Anyone know why this is?

I'm running from an external hard drive if that makes a difference.

---

### Post by treehugger on 2008-11-29
> **Hydrohs said:**
> I have two monitors set up, I configure them with NVIDIA X Server Settings and everything is good (I'm running them with TwinView) until I log off or restart. Then my second monitor gets disabled, and I have to manually re-apply the settings every time. Anyone know why this is?

I'm running from an external hard drive if that makes a difference.

Hello Hydrohs. Well, what I did was to change my /etc/X11/xorg.conf file to use the res and refresh i wanted. what I noticed was that even though the preferences app would save your setting, it would always put the default setting of 60hz back in front of the preferences that the application set.

mine looks like this now

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips 190S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024_75 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The bottom > Section "Screen" the line containing..
* Option         "metamodes" "1280x1024_75 +0+0; nvidia-auto-select +0+0"
That line is what decides wht gets loaded for prefs. it is seperated by a semi-colon. The first half gets loaded, if it can't load it, then it trys the second half of the string after the semi-colon.
The prefs app would put the second half "nvidia-auto-select +0+0"" first every time. So defaults of 1280x1024_60 would get loaded. Just switch them around, then lock the file. You should be ok after that.
Yours will vary based on your hardware of course, but you might be able to use this as a template to adjust your config file. Once you get it the way you want, back it up, and then write protect it. Hope this helps.

---

### Post by Hydrohs on 2008-11-29
I took a look at the file, and nothing about my second monitor was there. So I went back into my NVIDIA settings and figured out that I needed to save the configuration file, and then save the X Configuration file for it to work. It's all working good now, thanks for your help.

---

