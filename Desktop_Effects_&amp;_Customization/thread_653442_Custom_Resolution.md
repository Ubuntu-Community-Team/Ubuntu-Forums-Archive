---
title: "Custom Resolution"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by Penguin Power on 2007-12-29
I'm trying to set my 2405FPW 1920x1200 screen to a resolution of 1920x1080, anyone know how i would achieve this? Attempts to edit xorg.conf have resulted in a complete lack of user interface :(

---

### Post by chewearn on 2007-12-29
What graphics hardware do you have?

---

### Post by hhhhhx on 2007-12-30
Get and install Envy, if your using Mint it will be pre-installed for you

---

### Post by Penguin Power on 2007-12-30
The graphics card is a nVidia 7950GT; pci-e, HDCP compatible.

The monitor is a Dell/Samsung 2405FPW and is not HDCP compatible but I can't see why that would be a problem. Does DVI only accept a variety of resolution modes, not custom ones? If that is the case, is there any way i can use 1920x1200 and configure a dead black area at the top and bottom of the screen?

---

### Post by chewearn on 2007-12-30
> **Penguin Power said:**
> The graphics card is a nVidia 7950GT; pci-e, HDCP compatible.

The monitor is a Dell/Samsung 2405FPW and is not HDCP compatible but I can't see why that would be a problem. Does DVI only accept a variety of resolution modes, not custom ones? If that is the case, is there any way i can use 1920x1200 and configure a dead black area at the top and bottom of the screen?

Quick questions:
Have you install nvidia restricted driver?
Did you use nvidia-settings to set-up your resolution?

---

### Post by Penguin Power on 2007-12-30
Yes and yes.

---

### Post by Forlong on 2007-12-30
You should post your xorg.conf: ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's CODE tag please (# button)

---

### Post by Penguin Power on 2007-12-30
Here you go. I hope my messing around with it the last couple of days hasn't disfigured it too much...

```


Section "ServerLayout"

    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbVariant" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Dell 2405FPW"
    HorizSync       30.0 - 130.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       15.0 - 70.0
    VertRefresh     49.0 - 71.0
EndSection

Section "Device"
    Identifier     "7950GT"
    Driver         "nvidia"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "7950GT"
    Monitor        "Dell 2405FPW"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1920x1200"
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
EndSection


```

---

### Post by Forlong on 2007-12-30
I reckon you already tried changing this
```
    SubSection     "Display"
        Modes      "1920x1200"
    EndSubSection
```
to 
```
    SubSection     "Display"
        Modes      "1920x1080"
    EndSubSection
```

---

### Post by Penguin Power on 2007-12-31
Yes, and it didn't change anything. I think i may have added that myself, realised it did bugger all, and forgot to take it out again.

Any other ideas? :)

---

