---
title: "screen resolution &quot;1024x768&quot;"
date: 2009-01-05
forum: General Help
---

### Post by xpoff on 2009-01-05
Hey Y'all

I have just got my s video working witch i'm really stoked on!
The prob i'm having is that I can't get my screen res "1024x768"
back.  I only have "800x600" "640x480" in my screen resolutions.
I have tryed to add "1024x768" in my x, but still no go,
I have to change my x every time i want to watch s video witch is kind of crap!
i'll post x 
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "Device"
    Identifier "SVIDEO"
    Driver "i810"
    Option "MonitorLayout"    "TV,LFP"
    Option "FlipPrimary" "True"
    Option "TVStandard"    "NTSC"
    Option "TVOutFormat"    "SVIDEO"
    Option "ConnectedMonitor"    "TV"
    Option "Clone" "True"
    BusID "PCI:0:2:0"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "TV"
    HorizSync    30-50
    VertRefresh    60
EndSection

Section "Screen"
    Identifier    "LCD"
    Device        "LCD"
    Monitor        "LCD"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "TV"
    Device        "SVIDEO"
    Monitor        "TV"
    DefaultDepth    24

    SubSection "Display"
        Depth    24
        Modes    "800x600" "640x480" "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "LCDandTV"
    Screen        "TV"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    Option         "AIGLX" "true"
EndSection

Section "ServerFlags"
    Option        "DefaultServerLayout" "LCDandTV"
EndSection
 
any help would be kick ***

Thanx Dicker

---

### Post by jocko on 2009-01-05
Make  a backup of your xorg.conf and try changing this part:
```
Section "Screen"
Identifier "LCD"
Device "LCD"
Monitor "LCD"
DefaultDepth 24
[COLOR=Blue]SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "800x600" "640x480"
EndSubSection[/COLOR]
EndSection

```Into this:
```
Section "Screen"
Identifier "LCD"
Device "LCD"
Monitor "LCD"
DefaultDepth 24
[COLOR=Blue]SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection[/COLOR]
EndSection
```And if you want your TV to be 1024x768, I think you need to change this:
```
Section "Screen"
    Identifier    "TV"
    Device        "SVIDEO"
    Monitor        "TV"
    DefaultDepth    24

    SubSection "Display"
        Depth    24
        Modes[COLOR=Red]    "800x600" "640x480" "1024x768"[/COLOR]
    EndSubSection
EndSection
```
Into this:
```
Section "Screen"
    Identifier    "TV"
    Device        "SVIDEO"
    Monitor        "TV"
    DefaultDepth    24
SubSection "Display"
        Depth    24
        Modes [COLOR=Red]"1024x768" "800x600" "640x480"[/COLOR]
    EndSubSection
EndSection
```

---

### Post by xpoff on 2009-01-05
Thanx for the quick reply!
I just gave that one a go and x started fine but still no "1024x768", it restarted in 800 x 600.  i think i might have to do W lcd mabe not supporting "1024x768"?, i'll keep lookin into it, thanx again
Dicker

---

