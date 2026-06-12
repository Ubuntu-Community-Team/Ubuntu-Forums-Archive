---
title: "What are my options for ATI dual head monitor setup?"
date: 2005-11-21
forum: Desktop Environments
---

### Post by juliott on 2005-11-21
Hi,

I have a laptop with a ATI Mobility X300 (built-in LCD, 1x RGB-out, TV-out) that supports a resolution of 1400x1050. I also have an external 17" flatscreen that supports 1280x1024.

What are my options concerning a dual head setup under Ubuntu under these conditions?

I've tried ATI proprietary driver and the "Big Desktop", but this forces me to use the same resolution on both monitors (using the lowest denominator) which means that I haveto use 2x1280x1024. Now, this is probably better than using just 1400x1050 if you consider only screen-real estate.. but I am used to working at much higher resolutions and have a hard time coping with everything being so .. big :)

I've also tried setting up two $DISPLAYS. This allows me to run custom resolutions on the two monitors, but I get loads of crashes (gnome-panel and widgets).. and it does not support interoperability (I cannot move applications between screens, apps cannot communicate over $DISPLAYS (not without tweaks anywho) etc).

Is there an option to mimic the .. gasp .. behaviour in windows xp? I "simply" want to extend my destop to another monitor running at a different resolution.

I do not forsee any need for 3D hardware acceleration, so I can use the ubuntu (open) ati driver if necessary.

I've been searching these forums, google and mailing lists.. but information is both sparse and overwhelming at the same time. Any pointer to sources of applicable information would be greatly appreciated.

Thanks in anticipation :)

[B]Update: I managed to solve this one myself. I used the "radeon" drivers with MonitorLayout "LFP, CRT", and added screen numbers.  This seems to have done the trick. Sorry to have wasted space! :)

xorg.conf (updates in bold):
[/B]Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "se"
EndSection

Section "InputDevice"
    Identifier    "Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
    Driver        "radeon"
**    Option        "MonitorLayout" "LFP, CRT"**
    BusID            "PCI:1:0:0"
**    Screen        0**
    Option       "AGPMode" "4"
    Option       "AGPFastWrite" "on"
    Option       "BusType" "AGP"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility M300 (M22) 2"
    Driver        "radeon"
    BusID            "PCI:1:0:0"
**    Option        "MonitorLayout" "LFP, CRT"**
**    Screen        1**
    Option       "AGPMode" "4"
    Option       "AGPFastWrite" "on"
    Option       "BusType" "AGP"
EndSection

Section "Monitor"
    Identifier    "Laptop Monitor"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "External Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Laptop Screen"
    Device        "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
    Monitor        "Laptop Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1400x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "External Screen"
    Device        "ATI Technologies, Inc. Radeon Mobility M300 (M22) 2"
    Monitor        "External Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x1024"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Dual Head Layout"
    Screen    **0**    "Laptop Screen" 0 0
    Screen    **1**    "External Screen" RightOf "Laptop Screen"
    InputDevice    "Keyboard"
    InputDevice    "Mouse"
    InputDevice    "Touchpad"
    Option        "Clone" "off"
EndSection

Section "ServerLayout"
    Identifier    "Laptop Layout"
    Screen        "Laptop Screen"
    InputDevice    "Keyboard"
    InputDevice    "Mouse"
    InputDevice    "Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

---

### Post by juliott on 2005-11-22
For reference, this is confirmed to work on my Dell D610 with the ATI Mobility Radeon X300.

---

### Post by vito3434 on 2005-11-24
Hi, I've tried the same config, but with no luck.
I'm using 6.04 Dapper with a Thinkpad T41 Ati Radeon 9000
Ideally I would like to run the LFP Laptop Flat Panel at 1400x1050 and
the external DFP Desktop Flat Panel at a different resolution - 1024x768

I'm using the following config the LFP works fine, but the external secondary flat panel goes black.  I can mouse over to the secondary monitor, but since the flat panel is black, I can't see anything.  Am i missing something with Xinerama?  Help I'm dazed and confused.

xorg.conf
__________________________
Section "ServerFlags"
Option "Xinerama" "true"
EndSection

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "se"
EndSection

Section "InputDevice"
Identifier "Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility 9000"
Driver "radeon"
Option "MonitorLayout" "LFP, CRT"
BusID "PCI:1:0:0"
Screen 0
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "BusType" "AGP"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility 9000 2"
Driver "radeon"
BusID "PCI:1:0:0"
Option "MonitorLayout" "LFP, CRT"
Screen 1
Option "AGPMode" "4"
Option "AGPFastWrite" "on"
Option "BusType" "AGP"
EndSection

Section "Monitor"
Identifier "Laptop Monitor"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "External Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Laptop Screen"
Device "ATI Technologies, Inc. Radeon Mobility 9000"
Monitor "Laptop Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1400x1050"
EndSubSection
EndSection

Section "Screen"
Identifier "External Screen"
Device "ATI Technologies, Inc. Radeon Mobility 9000 2"
Monitor "External Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Dual Head Layout"
Screen 0 "Laptop Screen" 0 0
Screen 1 "External Screen" RightOf "Laptop Screen"
InputDevice "Keyboard"
InputDevice "Mouse"
InputDevice "Touchpad"
Option "Clone" "off"
EndSection

Section "ServerLayout"
Identifier "Laptop Layout"
Screen "Laptop Screen"
InputDevice "Keyboard"
InputDevice "Mouse"
InputDevice "Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by Grimlock on 2005-11-24
I set my dual head up (2nd monitor is a tv) Using sudo fglrxconfig. This was on my Radeon 9600Pro on Breezy.

---

### Post by tomski on 2005-12-12
only a knight that likes to NI would also say :

Micro$oft I fart in your general direction!!!

i wonder if they have a shrubery out side their windows??

---

### Post by Anonymaus on 2005-12-12
There's a new ATI driver out for some days now. Did anyone try it? Does it support dual head with a big desktop and different resolutions and refresh rates? I'd really like to have 3D support (which the OSS driver doesn't offer), but I just need the two screens ;) 

Oh, and switching xorg.conf's is no option. Tried it but it gets really annoying by the time.

---

### Post by DrBair on 2005-12-14
This is easily doable with the open source version of the radeon driver atleast, I should know as I've done it with my T30 which has a radeon 7500. I was able to do 1280x1024 (external) and 1024x768 (built-in).  Of course I haven't used it in a while since I got my shiny new desktop but I can tell you you will be needing the mergedfb option.  The metamodes option will also make your life much happier if you want to change the setup around frequently.  

Last I checked this will give you openGL on both screens, but overlays only on one screen.  You can charge which monitor gets the overlay by command, or by xorg.conf option.  

Heres the manual for the radeon module, [http://wiki.x.org/X11R6.8.0/doc/radeon.4.html](http://wiki.x.org/X11R6.8.0/doc/radeon.4.html)

---

### Post by iv0 on 2005-12-23
Hi everyone,

I spent few days on this with my Centrino laptop with Radeon 9600 MV350 (M10) graphics card + external CRT monitor attached. It didn't work for me (Ubuntu 5.10 Breezy). I tried:

[LIST]
[*]fglrx Dual Head worked fine, but I didn't like it neither (experiencing applet crashes)
[*]fglrx Big Desktop didn't work well (windows didn't place correctly, ended up between the monitors, couldn't make it work with 2 different resolutions 1400x1050 + 1280x1024)
[*]couldn't make the XORG radeon driver to work for xorg Big Desktop (laptop LCD always turned on, but it was black, even everything ran, I couldn't see anything on LCD)
[/LIST]

The solution was very strange - I had to switch in BIOS following option:
**Display** from "Detected" to "Both".

If anyone is interested, I can place here a copy of my xorg.conf (but it is almost identical to the Juliott's xorg.conf).

---

