---
title: "Cedega 5.1 and CS: Source performance"
date: 2006-02-16
forum: Gaming &amp; Leisure
---

### Post by eqisow on 2006-02-16
I have recently downloaded and installed Cedega 5.1 and am attempting to play Counter-Strike: Source. Everything installs and launches fine, but I am getting absolutely horrible performance in game. At 640x480 with all settings on low I get something like 20-30 FPS. Somewhere between 6 months and a year ago I got Windows level performance (with slight graphical glitching) on the same system and Ubuntu Hoary, so I know better is possible. All of the system test in Cedega pass. The Cedega settings for Steam are currently at default, though I feel like I have tried every possible combination of settings. I have also tried Cedega versions 5.0.2, 5.0.3, and 5.1. System specs are as follows:

AMD 64 3000+
2GB DDR400 RAM
GeForce 6800 (128 MB) using 81.87 drivers
Kubuntu Breezy running 2.6.12-10 686 kernel.
Xorg version 6.8.2

Xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"

#       Load    "GLcore"
    Load           "bitmap"
    Load           "ddc"
#       Load    "dri"
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
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"

#       Option          "UseFBDev"              "true"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo" "on"
    Option         "RenderAccel" "true"
    Option         "BackingStore" "On"
    Option         "NvAgp" "1"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Does anybody have any ideas on improving performance to something playable? Looking forward to hearing your input, thanks in advance.

---

### Post by eqisow on 2006-02-16
I have just noticed that under Advanced Video Options in CS: Source it shows the hardware DX level as 7. This (I think) means that it is emulating DX9 features on the software level, which is not good. I tried adding '-dxlevel 90' to the launch options for CS:S. After doing this the hardware DX level shows up as 9.0 under the options... until I actually enter a game, in which case the hardware DX level shows up as 7 again and the extreme laginess ensues. Does anybody think that this is, in fact, the problem? If it is, what could I do aout it?

---

### Post by fontis on 2006-02-17
Well tbh, you shouldnt expect better performance under linux atm. Since Cedega emulates windows DX engine.

Furthermore, the contradiction here is that you are actually supposed to get better FPS and overall performance by using dxlevel 70 than 90. Since 90 is only supported "fully" by the newest cards, and I doubt there is much support or value for those when running steam under linux.

---

### Post by eqisow on 2006-02-17
It's a reproduction of the Windows/DX API, not an emulator... performance is usually near windows level on supported games with Cedega, I've even seen cases where it was better.

As far as the DX level my card *is* a DX9 card. Also, what CS is showing is hardware DX level 7, but software DX level 9; which is what is leading me to believe that it is emulating DX9 features on a software level. May be wrong on the assumption, however...

Also, others have reported much better performance than what I'm getting and I've even seen it myself. I don't think it's unreasonable to expect a little more.

---

### Post by LordBug on 2006-02-17
Reading the forums today, I'm seeing other threads showing up talking about Cedega 5.1 blowing up 3D support.  Your situation might be related.

---

### Post by Peturrr on 2006-02-17
Your problem seems to be Xorg / driver related.

You have several options under the 'screen' section, that should be under the 'device' section. These are:
    Option         "NoLogo" "on"
    Option         "RenderAccel" "true"
    Option         "BackingStore" "On"
    Option         "NvAgp" "1"

Maybe this will fix the problem.

I assume you have already read the [HOWTO: latest nvidia drivers]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by eqisow on 2006-02-17
Lmao, so it would seem.... oops. Well unfortunately my entire X server is currently fubar'd, but I will try fixing that and see how it goes once things are running smoothly again.

Thanks Peturrr

(And yes, I did... in fact if you go to the end of the thread you'll see me witht he broken X server. ;) )

---

