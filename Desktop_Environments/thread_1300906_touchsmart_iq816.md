---
title: "touchsmart iq816"
date: 2009-10-25
forum: Desktop Environments
---

### Post by sklinemansk on 2009-10-25
i have some experience with Linux just for info. Recently purchased touchsmart Iq816 have got Ubuntu 9.04 everything working except having trouble with touchscreen. I have followed other topics with some success. Touchscreen seems to be partially working but not really that functional. I will post copy of xorg.conf for others to view and maybe help me out thanx..I have run the touchscreen calibrate program. The problem is touching the screen just loads trash file browser everytime. Just seems like simple configuration correction to me. Anyhelp appreciated.


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "touchscreen" "CorePointer
    InputDevice    "dummy"
EndSection

Section "Module"
    Load           "glx"
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
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event4"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

---

### Post by sklinemansk on 2009-10-25
well i played around a bit and seem to have solved the problem..seems to be the event of the touchscreen..will test further.





Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "touchscreen" "CorePointer"
    InputDevice    "dummy"
EndSection

Section "Module"
    Load           "glx"
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
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event7"
    Option "DeviceName" "touchscreen"
    Option "MinX" "1"
    Option "MinY" "1"
    Option "MaxX" "32768"
    Option "MaxY" "32768"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons" "false"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

---

