---
title: "Twinview + Seperate X, 3 screens, 2 GPU"
date: 2009-08-08
forum: Desktop Environments
---

### Post by unf on 2009-08-08
Hi,

I have 3 displays

VP171         2x17" with 8600GT
Sony 40W5500  1x40" with 8400GS

Jaunty + 185.19

So the problem is when I add the 40" Sony TV as Seperate X. The result is this:  

[Picture of 2x17"+40"]("")

When using only 2x17":

[Picture of 2x17"]("")

Gnome panel is too wide, and the fullscreen in the 40" is only 1280 pixels. When loggin in the login name is between the displays. EDIT: Also you can see a black stripe bottom of the 40" screen. 

Here is the difference between the xorg.conf files 

[QUOTE=Two displays only]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Monitor"

    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VP171b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection[/QUOTE]

[QUOTE=Three displays]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 1080
    Screen      1  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VP171b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       14.0 - 70.0
    VertRefresh     48.0 - 62.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/QUOTE]

---

### Post by unf on 2009-08-10
^^

---

### Post by nick5449 on 2009-08-15
I also just recently added a tv to my setup in the exact same way but am also experiencing the same issues.  Has anyone figured out a way to fix this?

Thanks

---

### Post by signseeker on 2009-08-16
Soooo, I'm assuming you want to retain twinview with the 2 17" monitors, and have a separate X session on the 40"?

Did you edit xorg.conf yourself? Or did you use nvidia-settings? 

I have a 22" LCD driven by a nvidia 8800GT and a 19" LCD driven by a nvidia 8600. I have 2 separate X-sessions and nvidia-settings did all the config work for me. 

It looks like your 40" screen is being treated like a part of your twinview set-up.

---

### Post by unf on 2009-08-17
> **signseeker said:**
> Soooo, I'm assuming you want to retain twinview with the 2 17" monitors, and have a separate X session on the 40"?

Did you edit xorg.conf yourself? Or did you use nvidia-settings? 

I have a 22" LCD driven by a nvidia 8800GT and a 19" LCD driven by a nvidia 8600. I have 2 separate X-sessions and nvidia-settings did all the config work for me. 

It looks like your 40" screen is being treated like a part of your twinview set-up.
The two setup are created with nvidia-settings-185. 

Screen 0 "Screen0" 0 1080
Screen 1 "Screen1" 0 0

Option "TwinView" "0"

I dont understand why there is only two "Screen (0-1)" I have tried to add another "Screen" so Screen 0 Screen 1 and Screen 2. No luck with that. 

Or is the Twinview only one Screen 0? Yes I know the resolution for the twinview setup is 2560x2048 is it kind of "virtual screen" Another problem with the blinking if I change the resolution with Sony TV? If I reboot its gone. So is this a bug with the nvidia-settings?

So I dont really understand how this works, because if I dont have the twinview I cannot move "windows" between the screens.

---

### Post by Seinfeld on 2011-05-11
Hi..

My problem is somehow similar. I am using 2 Nvidia 9600 and 8600 cards. I have two monitors running in TwinView with no problem on the first card.
When I added a third monitor to use as a separate x screen, connected to the second card, it worked but the Twin View switches to Xinerama. The first card sees the first two screens as one spreads the view on two monitors. Isn't that Xinerama?? I did disable xinerma from nvidia settings, restarted xserver but, no way.
I Just need two monitors working in a TwinView on the first card and the third one connected to the second card as a separate screen..
Any help please is much appreciated..

Thank you very much

Here is my xorg.conf with the 3rd monitor enabled..


```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 04:59:45 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    Driver         "keyboard"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP LP2465"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA703 SERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by unf on 2011-05-11
> **Seinfeld said:**
> Hi..

My problem is somehow similar. I am using 2 Nvidia 9600 and 8600 cards. I have two monitors running in TwinView with no problem on the first card.
When I added a third monitor to use as a separate x screen, connected to the second card, it worked but the Twin View switches to Xinerama. The first card sees the first two screens as one spreads the view on two monitors. Isn't that Xinerama?? I did disable xinerma from nvidia settings, restarted xserver but, no way.
I Just need two monitors working in a TwinView on the first card and the third one connected to the second card as a separate screen..
Any help please is much appreciated..

Thank you very much

Here is my xorg.conf with the 3rd monitor enabled..


Dude this is 2011 I wrote this in 2009! :D 

U could try this one, change the monitors and devices and remove RANDR + Rotate

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@actinium)  Wed Dec 23 23:28:57 UTC 2009

Section "Module"
	Load		"glx"
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    #Option         "Xinerama" "1"
EndSection

Section "Files"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP LP2475w"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ViewSonic VP171s"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "ViewSonic VP171b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    Option "AddARGBGLXVisuals" "true"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:6:0:0"
    Option "AddARGBGLXVisuals" "true"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:6:0:0"
    Option "AddARGBGLXVisuals" "true"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "RandRRotation" "on"
    Option         "Rotate" "CCW"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "RandRRotation" "on"
    Option         "Rotate" "CCW"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RANDR" "Enable"
EndSection

```

---

### Post by Seinfeld on 2011-05-12
Hi.. What can I say?? Your knowledge stays for years for everyone to enjoy :):D.. Thanks 
I actually looked at your file and took me sometime to try.. It did not work, however, I tried something I could get from your approach in the file my friend..
The solution is simple, just 1. Forget about TwinView, 2. Let every monitor set a separate X screen 3. Enable Xinerama.. 

This really works fine. But could I make the third monitor which is connected to the second card, a separate screen ??

Here is my current xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1920 0
    Screen      2  "Screen2" 3320 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP LP2465"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2017"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA703 SERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

