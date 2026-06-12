---
title: "Mouse and keyboard not working!"
date: 2010-11-05
forum: Desktop Environments
---

### Post by cci[RR]us on 2010-11-05
Hi,

I messed up my xorg.conf and tried to put in a clean one, but it doesn't seem to work. I'm not sure what went wrong. When X loads, the mouse cursor is not responding and my keyboard is dead too. I can't toggle to text mode either (Alt-Ctrl-F1).

Hope the following files might explain what's wrong.

/var/log/Xorg.0.log
```

[    26.835] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    26.840] (II) No input driver/identifier specified (ignoring)
[    26.841] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    26.841] (II) No input driver/identifier specified (ignoring)
[    26.841] (II) config/udev: Adding input device Fujitsu FUJ02B1 (/dev/input/event5)
[    26.841] (II) No input driver/identifier specified (ignoring)
[    26.842] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.842] (II) No input driver/identifier specified (ignoring)
[    26.842] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    26.842] (II) No input driver/identifier specified (ignoring)
[    26.847] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    26.847] (II) No input driver/identifier specified (ignoring)
[    26.847] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    26.847] (II) No input driver/identifier specified (ignoring)
**[    26.847] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)**
[    26.847] (II) No input driver/identifier specified (ignoring)

```

/etc/X11/xorg.conf
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "glx"
        Load  "record"
        Load  "dbe"
        Load  "extmod"
        Load  "dri2"
        Load  "dri"
EndSection

[b]Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection[/b]

[b]Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection[/b]

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"               # [<str>]
        #Option     "DRI"                       # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "VideoKey"                  # <i>
        #Option     "FallbackDebug"             # [<bool>]
        #Option     "Tiling"                    # [<bool>]
        #Option     "Shadow"                    # [<bool>]
        #Option     "SwapbuffersWait"           # [<bool>]
        #Option     "XvMC"                      # [<bool>]
        #Option     "XvPreferOverlay"           # [<bool>]
        #Option     "DebugFlushBatches"         # [<bool>]
        #Option     "DebugFlushCaches"          # [<bool>]
        #Option     "DebugWait"                 # [<bool>]
        #Option     "HotPlug"                   # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection


Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I'm running 10.10 x86. Please assist. Thank you!

---

### Post by P4man on 2010-11-05
I cant immediately spot the error in your xorg.conf, but try renaming it. You dont need a xorg.conf anymore, so without one I suspect at least keyboard and mouse will work fine again.

---

### Post by cci[RR]us on 2010-11-05
> **P4man said:**
> I cant immediately spot the error in your xorg.conf, but try renaming it. You dont need a xorg.conf anymore, so without one I suspect at least keyboard and mouse will work fine again.
I did that. Same thing happens. I suspect there is another xorg.conf that is invalid and causing the problem.

Where should I be looking for the bad config files?

Or is this caused by a faulty "intel" driver? I was fiddling around to get Compiz working. I tried using "vesa" but it didn't work (no screens found).

---

### Post by P4man on 2010-11-05
If you dont have a xorg.conf now, then I suspect the problem is elsewhere entirely. Do you have functional mouse and keyboard in the login screen?

---

### Post by cci[RR]us on 2010-11-05
> **P4man said:**
> If you dont have a xorg.conf now, then I suspect the problem is elsewhere entirely. Do you have functional mouse and keyboard in the login screen?
There is no login screen because I had set it to auto login. I do not see any login screen upon boot up. The next thing I know I'm already inside my desktop. The desktop is "alive" as my clock is moving.

How do I "reset" all my X settings to default, to revert to the settings that worked since day one? I tried X -configure but it doesn't help.

---

### Post by cci[RR]us on 2010-11-05
Does this mean I need to format and install Ubuntu again? Just to get X working? :(

---

### Post by azertyh on 2010-11-06
hello,
the doc about touchpad : [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by cci[RR]us on 2010-11-06
> **azertyh said:**
> hello,
the doc about touchpad : [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
Thanks but I'll check it out later. But what about my keyboard?

---

