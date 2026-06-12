---
title: "Xorg.conf very basic"
date: 2010-02-14
forum: Desktop Environments
---

### Post by toaksie on 2010-02-14
Just installed the restricted drivers for my ATI card, which shows up fine in lspci:

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

however my xorg.conf looks like this 


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

which i believe is causing me problems when i am trying to run compiz and emerald in Ubuntu 9.10 x64.  Any help much appreciated.

---

### Post by labinnsw on 2010-02-21
I am not totally comfortable with the xrandr workings, but I believe [this link]("https://wiki.ubuntu.com/X/Config/Resolution") will provide some assistance.

---

### Post by Hero of Time on 2010-02-21
Here is my xorg.conf with an nVidia card. You have to change the driver to the ATi one. If you have problems running compiz, it's best to run it from the command line and google the errors you get.
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"        0 0
        InputDevice     "Logitech MX510"
EndSection

Section "ServerFlags"
        Option  "BlankTime"     "15"
        Option  "StandbyTime"   "15"
        Option  "SuspendTime"   "15"
        Option  "OffTime"       "15"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "altgr-intl"
        Option          "XkbOptions"    "lv3:ralt_switch:altwin:meta_win"
EndSection

Section "InputDevice"
        Identifier  "Logitech MX510"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5"
        Option          "ButtonMapping" "1 2 3 8 9 4 5 10"
EndSection

Section "Monitor"
        Identifier      "BenQ"
        Option          "DPMS"  "True"
EndSection

Section "Device"
        Identifier      "nVidia GeForce 7800 GTX"
        Driver          "nvidia"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia GeForce 7800 GTX"
        Monitor         "BenQ"
        DefaultDepth    24
        SubSection      "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
```
Some other sections need to be changed for you too, like the resolution and input devices. I don't think you have an MX510. You can even leave out the input device sections.

---

### Post by aarons6 on 2010-02-22
> **toaksie said:**
> Just installed the restricted drivers for my ATI card, which shows up fine in lspci:

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

however my xorg.conf looks like this 


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

which i believe is causing me problems when i am trying to run compiz and emerald in Ubuntu 9.10 x64.  Any help much appreciated.

i  have a hd 3650 and i cant run compiz and emerald, i think its a driver issue.. 
also turning on the defualt xfce4 effects comes up with an error, effects cant be enabled at this time.

---

