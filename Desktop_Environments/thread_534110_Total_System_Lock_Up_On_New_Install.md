---
title: "Total System Lock Up On New Install"
date: 2007-08-24
forum: Desktop Environments
---

### Post by ADRegner on 2007-08-24
I am in the process of ditching Windoze completely and there is just one major hang up between me and pure Ubuntu-flavored bliss.

First, some preliminary information:  I have a 19-inch Viewsonic CRT monitor capable of 1600x1200 and a 17-inch Acer LCD monitor capable of 1280x1024.  I want to use them both at those respective resolutions in an extended-desktop layout.  (just like windows... not spanning one desktop over both with TwinView.)  I would also like to have compiz fusion working right, but that is not a priority at the moment.  My video card is an Asus GeForce 7200GS with 128 MB on-board RAM and an additional 384 “borrowed” from the system's RAM.  (When I get around to figuring out how, I will disable that feature and it will just use the on-board 128.)  Rest is, Asus P5N32-E  SLI motherboard, Core2 Duo 6750 CPU, 2 GB Crucial Ballistix RAM, Seagate 500 SATA 3.0 HDD.

The problem is the screen and (quickly after) the entire system locking up to the point there it will not even toggle the caps lock, move the cursor or respond to a network ping.  It occurs between 6 and 120 minutes (never longer) after I have logged in.  It seems to happen at “random.” and from what I can tell only when I am logged into GNOME.  I have noticed that it seems to be fine when it is just sitting at the login prompt before GNOME, metacity, compiz, or anything else are started.  (for more then 3.5 hours based on my experiments.)  In several cases I have been able to ssh into my system the moment it freezes up, but only for a couple minutes at best.  I have installed and ran compiz fusion a couple of times and that seems to make it lock up sooner.  Once I start compiz, the system locks up less then 30 minutes after no matter what.  (compiz will not work at all or freeze the system in less then 4 minutes if I don't use --indirect-rendering.)  Also, I have set up duel head monitors with Xinerama enabled to get the layouts and capabilities I need, but the system will lock up in less then 30 minutes with that xorg.conf configuration.

Again, I need to get the duel monitors set up and working stable in the “ideal” xorg.conf attached below.  In a perfect world, I can also have compiz fusion working good along with that too.  I have also attached the xorg.conf file I am using now, with just one monitor enabled.  Any help would be much appreciated.  Thanks.

IDEAL extended desktop xorg.conf:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"

   # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "dbe"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic A90f+"
    HorizSync       30.0 - 86.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL1715"
    HorizSync       24.0 - 80.0
    VertRefresh     49.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1600x1200 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0; CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

CURRENT single-monitor xorg.conf:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"

   # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "dbe"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic A90f+"
    HorizSync       30.0 - 86.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1600x1200 +0+0; CRT: 1024x768 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0; CRT: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Just let me know if there is any more information I can provide.  I know my way around Linux well enough to get anything out of it, even if I only have a couple minutes before it locks up again... :(

---

### Post by ADRegner on 2007-09-12
Just for reference sake, this issue is just about solved.  I had the latest nVidia drivers for my card installed (100.14.11 i think)  but all the crashing and freezing stopped once I went to the nVidia beta driver website and downloaded what they had there.  It was a .bin which installed version 100.14.06 of the driver.  (I know that the number is not higher, as most beta driver's are, so I do not know what is going on exctally.  I just know that it works and thats what I get with glxinfo)  I had to reinstall the driver about a week after, so I hacked my way through the Envy source code and eventually got it to automatically install that driver direct from nVidia's website, instead of the one it was orginally programmed to install.  Everything has been working good for a couple weeks now.  I have even enabled Xinerama and that too works good.  (Except there is no compiz fusion anymore, but I will post a new thread asking for help on that later.  Will link to it below when I do.)

---

