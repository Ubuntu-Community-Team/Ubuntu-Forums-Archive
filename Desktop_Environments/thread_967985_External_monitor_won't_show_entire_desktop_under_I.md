---
title: "External monitor won't show entire desktop under Intrepid"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Ludachrispeed on 2008-11-02
After the upgrade to Intrepid my laptop displays things fine, but my external monitor cuts off a tiny bit of the left side of the screen. For examle, if a Firefox window is maximized, I can only read the "ile" part of the "File" menu's name. This is really annoying!

Laptop = Dell D820
External monitor = ViewSonic (vx2235wm)
Connection via a VGA/VGA cable
Graphics driver = NVIDIA accelerated graphics driver (version 177) (no problems activating this, the upgrade handled that well)

Both the laptop LCD and external monitor are set to 1680x1020 resolution, which is the preferred resolution for both.  I did this using the NVIDIA X Server Settings GUI (sudo nvidia-settings)

I've spent a while trying to change things in the nvidia-settings GUI, but nothing seems to work. My xorg.conf file looks different after the upgrade... I don't know what "HAL" is or why so much is commented out!

Tried running dpkg-reconfigure -phigh xserver-xorg with no success.

Here is my xorg.conf file:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
# commented out by update-manager, HAL is now used
#    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Generic Keyboard"
#    Driver         "kbd"
#    Option         "XkbRules" "xorg"
#    Option         "XkbModel" "pc105"
#    Option         "XkbLayout" "us"
#    Option         "XkbVariant" "dvorak"
#    Option         "XkbOptions" "lv3:ralt_switch"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Synaptics Touchpad"
#    Driver         "synaptics"
#    Option         "SendCoreEvents" "true"
#    Option         "Device" "/dev/psaux"
#    Option         "Protocol" "auto-dev"
#    Option         "HorizEdgeScroll" "0"
#EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2235wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 110M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1680x1050 +0+0, DFP: nvidia-auto-select +0+0"
EndSection



Thanks in advance,
Ludachrispeed

---

### Post by Ng Oon-Ee on 2008-11-02
To save time, I'll assume you know how to backup your xorg.conf and load the backup if things go badly wrong.

Anyway, the xorg.conf has a sort of tree structure. The ServerLayout uses Screen0, Screen0 uses Videocard0 and Monitor0 etc. etc. This means, firstly, that you can remove the Sections with identifiers Configure Monitor, Configured Video Device, and Default Screen. If you do not remove them, doesn't matter as well, but it normally helps to have a compact xorg.conf for your debugging.

I'd do that as a separate step, if you want (just comment them out, and restart to make sure things still work).

As for the 'real meat' of your question, I'd recommend changing this:-

```
Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "1"
Option "TwinViewXineramaInfoOrder" "DFP-0"
Option "metamodes" "CRT: 1680x1050 +0+0, DFP: nvidia-auto-select +0+0"
EndSection
```

to this:-

```
Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "1"
Option "TwinViewXineramaInfoOrder" "DFP-0"
Option "metamodes" "CRT: 1680x1050 +0+0, DFP: 1680x1050 +0+0"
EndSection
```

Just putting the resolution in directly instead of auto-select.

Also, your monitor also probably has some sort of menu to adjust the screen settings. Mess around inside that, I know on my own monitor I'm able to move the image left/right or up/down manually. This might solve your problem even without any of the above, most of which is really house-keeping anyway :)

---

### Post by buena on 2008-11-03
Try the following command in a terminal (when the external monitor is plugged in):
```
xrandr
```

Depending on or graphic card you will get an output of your available monitors. If you use an Intel card, you should find a device VGA (an ATI card should give VGA-0).
(This step was just to find out the "name" of your external monitor.)

Now you can set the correct position using xrandr:
```
xrandr --output VGA --pos 0x0
```
(Replace VGA by VGA-0 according to the output of the first step.)

If this solves your problem, you can add this code to your auto start programms. Like this, the correct position will also be available in your next sessions.

---

### Post by Ludachrispeed on 2008-11-03
Thank you all very much!

It was very nice to be able to simplify my xorg.conf file.

I feel kind of dumb - the problem was indeed solved by simply using the buttons on my monitor to compress the screen a little, and then move it to the right a little.

It was also nice to learn a little more about xrandr!

Thanks again,
Ludachrispeed

---

### Post by Ng Oon-Ee on 2008-11-03
> **Ludachrispeed said:**
> Thank you all very much!

It was very nice to be able to simplify my xorg.conf file.

You're welcome :p

> **Ludachrispeed said:**
> I feel kind of dumb - the problem was indeed solved by simply using the buttons on my monitor to compress the screen a little, and then move it to the right a little.

We've all made these little mistakes :p

---

