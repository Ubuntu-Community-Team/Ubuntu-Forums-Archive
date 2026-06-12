---
title: "Emerald Theme Manager Not working"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by pat23_2007 on 2007-08-18
[http://ubuntuforums.org/showthread.php?t=357501&page=1](http://ubuntuforums.org/showthread.php?t=357501&page=1)

Followed that guide to get Beryl on my system but the emerald theme manager is not working, i go to the beryl and select it as the windows decorator,  tried reloading it still won't work. Any Help please?

[http://crazystudio.org/images/Screenshot.png](http://crazystudio.org/images/Screenshot.png)

Pic to explain better, as you can see no title bars, or new theme added the theme that is their is smoked glass and is a regular gnome theme.

---

### Post by damansandhu on 2007-08-18
ok , have you installed your video card's drivers peroperly .

---

### Post by damansandhu on 2007-08-18
i am using kubuntu 7.04 and i have same problem as yours.

---

### Post by pat23_2007 on 2007-08-18
> **damansandhu said:**
> ok , have you installed your video card's drivers peroperly .

Yes, i have all drivers installed and working correctly.

---

### Post by damansandhu on 2007-08-18
ok i have same problem , try to set rendering platform in beryl manager options as aiglx and then xgl.

---

### Post by pat23_2007 on 2007-08-18
> **damansandhu said:**
> ok i have same problem , try to set rendering platform in beryl manager options as aiglx and then xgl.

I did, and when i put it on  XGL it just crashes and i have to reboot.

---

### Post by damansandhu on 2007-08-19
aha , totally same problem as mine.

---

### Post by Uber Nooblett on 2007-08-19
Same issue here. I had everything working fine up until today, and now neither Emerald or Heliodor will load up themes so I've had to revert back to Aquamarine.

I've tried backstepping all my changes, but no joy so far :(

Here is my xorg.conf if it helps:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
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
    HorizSync       32.5 - 80.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NUL"
    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024_75 +1280+0, CRT-1: 1280x1024 +0+0; CRT-0: nvidia-auto-select +1024+0, CRT-1: 1024x768 +0+0; CRT-0: nvidia-auto-select +800+0, CRT-1: 800x600 +0+0; CRT-0: nvidia-auto-select +640+0, CRT-1: 640x480 +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +1280+0, CRT-1: 1280x1024_75 +0+0; CRT-0: nvidia-auto-select +1024+0, CRT-1: 1024x768 +0+0; CRT-0: nvidia-auto-select +800+0, CRT-1: 800x600 +0+0; CRT-0: nvidia-auto-select +640+0, CRT-1: 640x480 +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-1: 1280x1024_75 +0+0; CRT-1: 1024x768 +0+0; CRT-1: 800x600 +0+0; CRT-1: 640x480 +0+0"
# Removed Option "metamodes" "CRT-0: NULL, CRT-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: nvidia-auto-select +0+0, TV: NULL"
# Removed Option "metamodes" "CRT-0: 1280x1024_75 +1280+0, CRT-1: 1280x1024 +0+0, TV: NULL; CRT-0: 1280x1024_75 +1280+0, CRT-1: nvidia-auto-select +0+0, TV: NULL"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +1280+0, CRT-1: 1280x1024_75 +0+0; CRT-0: 1280x1024_75 +1280+0, CRT-1: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +1280+0, CRT-1: 1280x1024_75 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
EndSection

```

---

### Post by damansandhu on 2007-08-19
i dont know what is the problem as i am having same problem , but today i installed it on my friends pc and it was working there.

---

