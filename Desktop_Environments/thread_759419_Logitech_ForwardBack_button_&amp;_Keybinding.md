---
title: "Logitech Forward/Back button &amp; Keybinding"
date: 2008-04-19
forum: Desktop Environments
---

### Post by Taragine on 2008-04-19
Hello,

As a preface, I must admit that I am a newbie when it comes to linux. I do have some experience, but I'd limit it to around 1 month. On this particular issue, II have looked at many threads for support on the issue, specifically:
[http://ubuntuforums.org/showthread.php?t=59729](http://ubuntuforums.org/showthread.php?t=59729)
and 
[http://locoteam.ubuntuforums.org/showthread.php?t=485175](http://locoteam.ubuntuforums.org/showthread.php?t=485175)

I think the most annoying aspect of this is that after a format, the mouse has lost its capability with the forward/back side buttons on an MX900 mouse.

I believe the problem occurred when I tried the first tutorial and the chmod 775 command (I don't know how to undo this command). I think, for some reason, evdev screwed it up. I have tried multiple button configurations to no avail. Here is my current settings: 

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
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
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "auto"
    Option 	   "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7 4 5 6"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2208WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M]"
    Driver         "nvidia"
    VideoRam        262144
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1680x1050" "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
EndSection

```
I have attached my entire xorg.conf code just in case if another section of xorg has conflicts with the mouse.

Please note that I have tried xbindkeys, evdev, and reconfiguring XORG. Sometimes I get some response from the side buttons like it duplicating the side buttons, but I'm not too sure. Also, these buttons work in WinXP, so that rules out hardware problems.

If you can please help me on this issue, that would be great.

Thanks

---

