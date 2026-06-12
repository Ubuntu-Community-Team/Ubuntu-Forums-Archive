---
title: "Nvidia Driver Woes..."
date: 2006-09-22
forum: Desktop Environments
---

### Post by aknapp on 2006-09-22
I have exhausted my brain, so now I bring my problem to you genius'

Here's a dump of my Xorg.0.log + Xorg.conf:

> **Xorg.0.log](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module said:**
> 

[QUOTE=Xorg.conf]
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
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

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 80.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x768" "1024x768" "800x600"
    EndSubSection
EndSection

This is after I have done a dpkg-reconfigure xserver-xorg. I installed my Nvidia driver using the envy script found here on these forums. I have tried purging everything and starting fresh, but nothing seems to take. Thanks.

---

### Post by ART_Adventures on 2006-09-22
I never could get my nvidia driving working. Whenever I boot Ubuntu I need to use Vesa mode in 1280x1024. It looks nice until you decide to watch a dvd, a video or something, and then the frame rate lag becomes noticeable.

I tried many things to get my nvidia card working; I spent the whole weekend doing it and nothing came of it.

If I somehow find the solution, I'll let you know, and please do the same for me.

Thanks.

---

### Post by aknapp on 2006-09-22
> **ART_Adventures said:**
> I never could get my nvidia driving working. Whenever I boot Ubuntu I need to use Vesa mode in 1280x1024. It looks nice until you decide to watch a dvd, a video or something, and then the frame rate lag becomes noticeable.

I tried many things to get my nvidia card working; I spent the whole weekend doing it and nothing came of it.

If I somehow find the solution, I'll let you know, and please do the same for me.

Thanks.

What model card do you have?

ie. I have a Geforce 6800 128MB

---

### Post by ART_Adventures on 2006-09-22
I have a GeForce FX5950 Ultra

---

### Post by fatsheep on 2006-09-22
I have a XFX 6600 GT and installed my Nvidia drivers with [Automatix](www.getautomatix.com).  I never messed with the scripts and binary installations so I can't help you on those but I would recommend you try automatix.

---

### Post by aknapp on 2006-09-22
> **fatsheep said:**
> I have a XFX 6600 GT and installed my Nvidia drivers with [Automatix](www.getautomatix.com).  I never messed with the scripts and binary installations so I can't help you on those but I would recommend you try automatix.

Ooo, forgot all about using automatix, will try that. Thanks.

---

