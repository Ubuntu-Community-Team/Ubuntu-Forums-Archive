---
title: "Ubuntu feisty fawn, inspiron 8200 and touchpad not working..."
date: 2007-08-06
forum: Dell  Ubuntu Support
---

### Post by flambeur on 2007-08-06
Hi!
I just installed ubuntu feisty fawn on my old Dell Inspiron 8200.
The trackpad don't work at all (cursor is at the middle of the screen and don't move...)

I tried a lot of things, installing synaptics drivers, configuring /etc/X11/xorg.conf
running gsynaptics....

But nothing worked....

Here's an excerpt of my xorg.conf:
```
Section "Module"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "dri"
    Load "extmod"
    Load "freetype"
    Load "glx"
    Load "int10"
    Load "vbe"
    Load "synaptics"
    Load "dbe"
    Load "record"
    Load "type1"
EndSection

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "HorizScrollDelta" "0"
    Option "SHMConfig" "on"
EndSection
```

Could someone help me? :)

---

