---
title: "DualScreen, TwinView, Rotate one display"
date: 2009-12-08
forum: Desktop Environments
---

### Post by Vegar on 2009-12-08
I just installed Ubuntu 9.10, and i just wanna say congratz. It's awesome :)

But, as always.. Things can get a little tricky along the road to the perfect setup :)

Well, as you might get from the title, what I want to accomplish is:
[list]
[*]TwinView
[*]DualScreen
[*]Rotation (90 degrees right) on the secondary display.
[/list]

Now, I've been fooling a round for a while, but without any decent results.

_I've got_
[list]
[*]Nvidia 8800 GTS 512
[*]Driver: "NVIDIA accelerated graphics driver (version 185)"
[/list]
And this is my xorg.conf file
```

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The way I see it, my problem is that when you go for TwinView, the screens have the same id (screen0), which makes it a lot harder for someone like me to rotate just one of the screens.

Thanks in advance, Hope some of you got some knowledge on how to accomplish my dream setup :)

EDIT: Added an image that shows how my screens are set up.

---

### Post by Vegar on 2009-12-09
Bump

---

### Post by Vegar on 2009-12-10
b
u
m
p
?

---

### Post by Vegar on 2009-12-11
bump

---

### Post by Vegar on 2009-12-15
Great bump of justice

---

### Post by Vegar on 2009-12-18
Last bump before i give up :(

---

### Post by thodges999 on 2009-12-24
Hi there
Hope you are still watching, I found the answer [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=876891") post 4.

I have an nvidia card and proprietary driver with ubuntu 9.10. It works for me although its not using twinview. Hope this helps.
Regards

---

