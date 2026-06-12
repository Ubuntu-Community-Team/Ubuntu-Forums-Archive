---
title: "can't get my laptop's resolution right (Intel 855GM chipset)"
date: 2006-09-04
forum: Desktop Environments
---

### Post by paperdiesel on 2006-09-04
I'm running ubuntu 6.06 on my Gateway laptop, and I can't get the
display to go any higher than 800x600.  What am I doing wrong?

I use apt-get install 915resolution and my Xorg.0.log says this:

From /var/log/Xorg.0.log:
```

(II) I810(0): Monitor0: Using hsync range of 28.00-51.00 kHz
(II) I810(0): Monitor0: Using vrefresh range of 43.00-60.00 Hz
(II) I810(0): Not using mode "1024x768@60" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (800
-> 1024). (--) I810(0): Virtual size is 800x600 (pitch 1024)
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(==) I810(0): DPI set to (75, 75)

```




>From /etc/X11/xorg.conf:
```

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated
Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
        UseModes        "Modes0"
EndSection

Section "Modes"
        Identifier "Modes0"

# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768@60"  64.11  1024 1080 1184 1344  768 769 772 795
-HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated
Graphics Device"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

>From /etc/default/915resolution:
```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=54
#
# and set resolutions for the mode.
#
XRESO=1024
YRESO=768
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=32

```

Can someone help me out here?  How do I get 1024 x 768??

---

### Post by powder on 2006-09-04
Move your modeline into your Monitor section.  Here's mine as an example:

```
Section "Monitor"
	Identifier  "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	HorizSync    30.0 - 96.0
	VertRefresh  50.0 - 160.0
	# V-freq: 85.00 Hz  // h-freq: 85.99 KHz
	Modeline    "1280x960" 167.84  1280 1368 1576 1952   960  960  963 1011 -hsync +vsync
EndSection
```

---

### Post by paperdiesel on 2006-09-04
Ok I tried that, I still get the same error in my log file and my X session is still at 800x600.

Any more ideas?

---

### Post by CatKiller on 2006-09-05
> **paperdiesel said:**
> Any more ideas?

You could try taking out the @60 so that the mode is "1024x768". I've only used standalone graphics cards, and only toyed with xorg.conf a little, but the modes I've seen have always just specified the resolution in the mode description, and the refresh rate is handled elsewhere.

Oh, and you might try commenting out the BIT=32 line in /etc/default/915resolution, or changing it to BIT=24, since you aren't actually using a 32-bit colour depth in your xorg.conf.

---

### Post by paperdiesel on 2006-09-05
> **CatKiller said:**
> You could try taking out the @60 so that the mode is "1024x768". I've only used standalone graphics cards, and only toyed with xorg.conf a little, but the modes I've seen have always just specified the resolution in the mode description, and the refresh rate is handled elsewhere.

Oh, and you might try commenting out the BIT=32 line in /etc/default/915resolution, or changing it to BIT=24, since you aren't actually using a 32-bit colour depth in your xorg.conf.

I tried both of those ideas too, still stuck at 800x600.

Help!

---

