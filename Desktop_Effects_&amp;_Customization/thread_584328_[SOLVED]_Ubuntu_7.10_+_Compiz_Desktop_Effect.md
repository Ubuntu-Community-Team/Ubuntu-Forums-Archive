---
title: "[SOLVED] Ubuntu 7.10 + Compiz Desktop Effect"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by ldesilva on 2007-10-20
Hi all,

My problem is back again. The screen flickers every now and then and it is getting to irritate me. Without the desktop effects enabled, no problem. When it is enabled, my laptop screen flickers. I have attached my xorg.conf and hope that someone will be able to help me. My laptop has a NVidia GeForce GO7300 adapter.

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver        "nvidia"
    Busid        "PCI:1:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Horizsync    28-51
    Vertrefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    Option        "AIGLX"    "true"
    
    # Uncomment if you have a wacom tablet
    Inputdevice    "stylus"    "SendCoreEvents"
    Inputdevice    "cursor"    "SendCoreEvents"
    Inputdevice    "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option        "Composite"    "Enable"
EndSection
Section "Module"
    Load        "glx"
EndSection

---

### Post by 1337455 10534 on 2007-10-21
Do you have a tablet?
> ```

# Uncomment if you have a wacom tablet
Inputdevice "stylus" "SendCoreEvents"
Inputdevice "cursor" "SendCoreEvents"
Inputdevice "eraser" "SendCoreEvents"
Inputdevice "Synaptics Touchpad"
EndSection

```

Is that your screen resolution?
> ```

Modes "1024x768"

```

This seems to be your refresh rate:
> ```

Vertrefresh 43-60

```

I'm no expert... Sigh, I don't even know if this is the correct file to look for this type of errors in... Even if I did identify something correctly, I don't know how to fix it. I'm very sorry. (I go around answering Unanswered posts.)

---

### Post by ldesilva on 2007-10-22
> **1337455 10534 said:**
> Do you have a tablet?
[/code]

Is that your screen resolution?
[/code]

This seems to be your refresh rate:
[/code]

I'm no expert... Sigh, I don't even know if this is the correct file to look for this type of errors in... Even if I did identify something correctly, I don't know how to fix it. I'm very sorry. (I go around answering Unanswered posts.)

Yes, I have a tabletpc and the resolution is 1024x768.

---

### Post by DemiG0D on 2007-10-25
I have the same problem with the screen flickering at random times, if I reboot it'll fix the issue temporarily but it always seems to come back.  I have a compal hel80 notebook with a nvidia 7600go graphics card.

---

### Post by nickless on 2007-10-26
Same thing here... Dell Inspiron 9400 with an Nvidia 7900GS
:(
Found something here: [http://ubuntuforums.org/showthread.php?t=571785&highlight=screen+flickers](http://ubuntuforums.org/showthread.php?t=571785&highlight=screen+flickers)
It is said to be an nvidia drivers problem, read this post [http://ubuntuforums.org/showpost.php?p=3624148&postcount=7](http://ubuntuforums.org/showpost.php?p=3624148&postcount=7)
I have not tried it yet, but will soon... it looks promising :D

---

### Post by nickless on 2007-10-27
:guitar: seems to work

---

### Post by ldesilva on 2007-11-08
Thanks, it did work for me this time :)

---

### Post by Hussain on 2007-11-10
Thank god i didn't faced this problem again, as i did in 7.04 :)

---

