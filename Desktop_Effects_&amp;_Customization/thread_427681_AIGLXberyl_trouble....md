---
title: "AIGLX/beryl trouble..."
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by TerranAce007 on 2007-04-29
I have an x86_64 laptop with a mobility radeon 9700. A few days ago I was running OpenSuse 10.2 with fglrx, XGL, and compiz just fine, but I wanted to give the new Ubuntu a try since suse runs slowly on my laptop.

I am now running Kubuntu 7.04 x86_64. Last night, after configuring my new install, I had both compiz and beryl working with XGL and fglrx, but upon a reboot in the morning, it no longer works, and I can't figure out why.

I spent several hours earlier today messing with the fglrx drivers to no avail. I figured I'd try the open source driver, but I have the same exact issue. Though, I got the radeon driver working and have 3D acceleration, plus none of the occasional lockups from fglrx!

```

andrew@redlaptop:~$ glxinfo | head -n 5
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

I removed the fglrx driver, xgl, and compiz packages since I just want beryl on AIGLX. I followed the howtos and added the deb repo:

```
deb http://ubuntu.beryl-project.org/ feisty main
```

Then forced the specified 0.2.0 version of beryl-core:

```

sudo aptitude show beryl-core
Package: beryl-core
New: yes
State: installed
Automatically installed: yes
Version: 0.2.0~0beryl1
Priority: optional
Section: main/x11
...

```

I added beryl-manager to .kde/Autostart, and try to activate it, and I get this:
```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

beryl-xgl: Another window manager is already running on screen: 0
beryl-xgl: No manageable screens found on display :0.0

```

When using fglrx with XGL on Display :1, I the tests are all successful, but I get the same error about no manageable windows. I am Getting very frustrated with this not working! Ideas anyone?

Here is my xorg.conf

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "true"
        Option          "DisableGLXRootClipping" "true"
        Option          "AddARGBGLXVisuals" "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "EnablePageFlip" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
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
        Option          "AIGLX"  "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

---

### Post by TerranAce007 on 2007-04-29
Commenting out these lines in the xorg.conf fixed it:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "AGPMode" "4"
        Option          "AGPFastWrite" "true"
        Option          "DisableGLXRootClipping" "true"
        Option          "AddARGBGLXVisuals" "true"
        #Option         "AllowGLXWithComposite" "true"
        Option          "EnablePageFlip" "true"
EndSection

...

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        #InputDevice     "stylus" "SendCoreEvents"
        #InputDevice     "cursor" "SendCoreEvents"
        #InputDevice     "eraser" "SendCoreEvents"
        #Option          "AIGLX"  "true"
EndSection

```

---

