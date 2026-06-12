---
title: "Ubuntu Running slower than should"
date: 2006-06-22
forum: Desktop Environments
---

### Post by niffkin on 2006-06-22
I am relatively new to linux (have only been using it a few months) and have tried a few distros. I really like ubuntu because of how easy it is to work with, however for some reason I feel like it is running much slower than it should. The blue box that pops up around the icons when an app is opened takes a little while some time, and well frankly it doesn't seem to be running that fast. Also as a little side note when I shut down or even just shut down gdm, I do not get a console just a black screen. However when I am running recovery mode it works fine. 

I am running ubuntu on dell inspiron 9300 with a Pentium M 1.8ghz processor and a nvidia 6800 go video card. I do have the latest nvidia drivers installed, and glx gears does work properly however seems to be running at a rather low fps.

Below is attached my xorg.conf(just in case) and any help would greatly appreciated.

Thanks,
Andrew

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#       Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"              # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV41.8 [GeForce Go 6800]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Option	   "RenderAccel"	"true"
    Option         "NvAGP" "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV41.8 [GeForce Go 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

```

---

### Post by jan on 2006-06-22
Did you "enable" the nvidia drivers?

---

### Post by niffkin on 2006-06-22
Yes I did, and I just made sure of it.... Thanks for the response though, much appreciated.


I would really like to figure out why I just get a black screen when I exit gdm, instead of a console -- that might help.

---

