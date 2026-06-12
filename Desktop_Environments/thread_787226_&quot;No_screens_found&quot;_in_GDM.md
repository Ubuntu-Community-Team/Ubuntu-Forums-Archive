---
title: "&quot;No screens found&quot; in GDM"
date: 2008-05-08
forum: Desktop Environments
---

### Post by flatko on 2008-05-08
I'm using ubuntu studio, with installed generic kernel and ubuntu artwork... It's almost ubuntu, but with some studio settings.

When i tried to install nvidia propietary driver using envy, it installs nvidia-glx-new (i have nvidia 5200)

Driver don't appear in Hardware drivers, and i use nvidia-xconfig to enable the driver. When i try to start X, it says "no screens found" - i find myself with no graphical environment.
What's wrong? This is my xorg.conf after running nvidia-xconfig:


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,bg"
    Option         "XkbVariant" ","
    Option         "XkbOptions" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by flatko on 2008-05-08
Got it!
In some magic way, the driver appeared in Hardware Drivers and activating from there seems to work. It happened that way in Feisty - worked from Hardware Drivers, but giving errors from running nvidia-xconfig

---

