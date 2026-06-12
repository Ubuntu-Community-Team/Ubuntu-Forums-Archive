---
title: "Problems setting the resolution right after videocard broken"
date: 2009-11-04
forum: Desktop Environments
---

### Post by ilmalcom on 2009-11-04
Hi, this is my problem: today my Geforce 6200 broke down and for now I decided to not buy a new videocard, but to use the integrated one. I changed my xorg.conf to use "vesa" drivers rather than "nvidia" drivers, but I cannot set the resolution right: the optimal choice for my monitor would be 1440x900, but I can't select it from Gnome and I'm stuck on 1280x1024. What should I do?

This is my xorg.conf
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
# commented out by update-manager, HAL is now used
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Mouse0" "CorePointer"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "keyboard"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
	Modes	   "1440x900_60"
	Viewport   0 0
	Depth	   24
    EndSubSection
EndSection

```

---

### Post by ilmalcom on 2009-11-04
I tried following the instructions in this page:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

However, when I try to set the resolution, I get the following error:

xrandr: Configure crtc 0 failed

---

### Post by ilmalcom on 2009-11-04
After the previous change, I set the driver to "intel" and it worked perfectly

---

