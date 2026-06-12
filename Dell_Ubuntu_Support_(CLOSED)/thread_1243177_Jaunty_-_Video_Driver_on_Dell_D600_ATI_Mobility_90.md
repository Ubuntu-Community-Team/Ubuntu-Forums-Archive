---
title: "Jaunty - Video Driver on Dell D600 ATI Mobility 9000"
date: 2009-08-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dc5guy on 2009-08-18
All the information I've found is outdated.  I saw some users running Beryl back then which makes me want to use the correct or better driver for this card.  

Can someone please help me and point me in the right direction?  I would like the video rendering to be smoother.

I've tried a lot of stuff from the outdated info only to go back to a clean install of Ubuntu again because I won't be able to boot up again.  I know running Compiz is possible and people have done it.

---

### Post by Waappu on 2009-08-18
Hi

You could try this

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_original
gksudo gedit /etc/X11/xorg.conf
```

File should be empty.

Paste these lines end of file
```
Section "Device"
    Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
    Driver          "ati"
    # Hyödyllisiä kaikille ATI/AMD-korteille
    Option "AccelMethod" "EXA" # ilman tätä käytössä on ati-ajurilla toistaiseksi vanhempi XAA
    Option "DynamicClocks" "true" # virransäästöominaisuus joka ei ole oletuksena kytketty tällä hetkellä päälle
    # Seuraavat vain Mobility Radeon 9000 / 32MB näyttömuisti
    Option "FBTexPercent" "0" # oletus "50", "0" tarkoittaa että kaikki ylimääräinen muisti varataan EXA:lle. jos näyttömuistia on enemmän kuin 32MB, tätä ei kannattane käyttää.
    Option "GARTSize" "128" # AGP-muistin määrä, "128" voi olla tarpeen
    Option "AGPMode" "4" # AGP-nopeus, oletuksena usein "1". "4" varmistaa että AGP-siirtonopeus on riittävä kohtuullisen sulavaan Compizin käyttöön
    Option "DepthBits" "16" # vapauttaa lisää muistia muuhun käyttöön syvyyspuskurin kustannuksella, ei tunnu haittaavan peruskäytössä
    Option "AccelDFS" "true" # nopeuttaa 3D-työpöytää, joillain AGP-silloilla aiheuttaa ongelmia jonka takia oletus on "false"
    # Seuraava on luultavasti tarpeeton
    Option "EnablePageFlip" "true" # oletus "false", tuntuu toimivan ja teoriassa nopeuttaa jotain
 EndSection

```

log off and back in.

See if helps.

I take it from here and it did help on my friend laptop
[http://wiki.ubuntu-fi.org/3D-ty%C3%B6p%C3%B6yd%C3%A4n_nopeuden_optimointi_Radeon_Mobility_9000](http://wiki.ubuntu-fi.org/3D-ty%C3%B6p%C3%B6yd%C3%A4n_nopeuden_optimointi_Radeon_Mobility_9000)

---

### Post by pawhtiobo on 2009-08-20
Hi,

I also got a Dell D600 with a Radeon 9000 (RV250), and i'm able to get compiz and the effects running with this xorg.conf, also have other xorg.conf, with other configurations that also work, those are some performance tests i made, if u manage to solve your problem, them i can give you them.

[FONT=PrimaSans BT,Verdana,sans-serif]Section "ServerLayout"
Identifier     "X.org Configured"
InputDevice    "Synaptics Touchpad"
Screen      0  "Screen0" 0 0
InputDevice    "Mouse0" "CorePointer"
InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
RgbPath      "/usr/share/X11/rgb"
ModulePath   "/usr/lib/xorg/modules"
FontPath     "/usr/share/fonts/TTF"
FontPath     "/usr/share/fonts/OTF"
FontPath     "/usr/share/fonts/Type1"
FontPath     "/usr/share/fonts/misc"
FontPath     "/usr/share/fonts/75dpi/:unscaled"
EndSection

Section "Module"
Load  "xtrap"
Load  "extmod"
Load  "GLcore"
Load  "glx"
Load  "dri"
Load  "record"
Load  "dbe"
Load  "freetype"
Load  "type1"
EndSection

Section "InputDevice"
Identifier  "Keyboard0"
Driver      "kbd"
Option  "XkbLayout"  "pt"    ## KEYBOARD_MAP!
Option  "XkbModel"  "dell"    ## KEYBOARD_MODEL!
Option  "Xkbvariant"  ""    ## KEYBOARD_VARIANT!
EndSection

Section "InputDevice"
Identifier  "Mouse0"
Driver      "mouse"
Option            "Protocol" "auto"
Option            "Device" "/dev/input/mice"
Option            "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
 Identifier    "Synaptics Touchpad"
 Driver        "synaptics"
 Option        "SendCoreEvents"    "true"
 Option        "Device"            "/dev/psaux"
 Option        "Protocol"          "auto-dev"
 Option        "SHMconfig"         "true"
 Option        "HorizScrollDelta"  "0"
 Option        "VertEdgeScroll"  "1"
 Option        "TapButton1"  "1"
EndSection

Section "Monitor"
Option "DPMS"
DisplaySize 269 201 # 96 DPI @ 1024x768
Option "UseEdidFreqs" "1"
#DisplaySize          280   210    # mm
Identifier   "Monitor0"
VendorName   "SHP"
ModelName    "1398"
HorizSync 31.5-64
VertRefresh 40-90
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option     "NoAccel"                # [<bool>]
#Option     "SWcursor"               # [<bool>]
#Option     "Dac6Bit"                # [<bool>]
#Option     "Dac8Bit"                # [<bool>]
#Option     "BusType"                # [<str>]
#Option     "CPPIOMode"              # [<bool>]
#Option     "CPusecTimeout"          # <i>
#Option     "AGPMode"                # <i>
Option     "AGPFastWrite"        "True"
#Option     "AGPSize"                # <i>
Option     "GARTSize"            "64"
#Option     "RingSize"               # <i>
#Option     "BufferSize"             # <i>
#Option     "EnableDepthMoves"       # [<bool>]
#Option     "EnablePageFlip"         # [<bool>]
#Option     "NoBackBuffer"           # [<bool>]
#Option     "DMAForXv"               # [<bool>]
#Option     "FBTexPercent"           # <i>
#Option     "DepthBits"              # <i>
#Option     "PCIAPERSize"            # <i>
#Option     "AccelDFS"               # [<bool>]
#Option     "DDCMode"                # [<bool>]
#Option     "IgnoreEDID"             # [<bool>]
#Option     "DisplayPriority"        # [<str>]
#Option     "PanelSize"              # [<str>]
#Option     "ForceMinDotClock"       # <freq>
#Option     "ColorTiling"            # [<bool>]
#Option     "VideoKey"               # <i>
#Option     "RageTheatreCrystal"     # <i>
#Option     "RageTheatreTunerPort"     # <i>
#Option     "RageTheatreCompositePort"     # <i>
#Option     "RageTheatreSVideoPort"     # <i>
#Option     "TunerType"              # <i>
#Option     "RageTheatreMicrocPath"     # <str>
#Option     "RageTheatreMicrocType"     # <str>
#Option     "ScalerWidth"            # <i>
#Option     "RenderAccel"         "True"
#Option     "SubPixelOrder"          # [<str>]
#Option     "ShowCache"              # [<bool>]
#Option     "DynamicClocks"          # [<bool>]
#Option     "VGAAccess"              # [<bool>]
#Option     "ReverseDDC"             # [<bool>]
#Option     "LVDSProbePLL"           # [<bool>]
Option     "AccelMethod"         "XAA"
Option     "DRI"                 "True"
#Option     "ConnectorTable"         # <str>
#Option     "DefaultConnectorTable"     # [<bool>]
#Option     "DefaultTMDSPLL"         # [<bool>]
#Option     "TVDACLoadDetect"        # [<bool>]
#Option     "ForceTVOut"             # [<bool>]
#Option     "TVStandard"             # <str>
#Option     "IgnoreLidStatus"        # [<bool>]
Identifier  "Card0"
Driver      "radeon"
VendorName  "ATI Technologies Inc"
BoardName   "Radeon RV250 [Mobility FireGL 9000]"
BusID       "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport   0 0
Depth     1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "on"
EndSection

The options in the Xorg, you can test it as you want, uncomment the ones you like and put the right flag...but you should be able to get compiz and all the effects with the default xorg, made by the instalation, you just need de enable the Extra effects in the apearance menu.
You dont need to reinstall the OS everytime you got the xorg broken, just start Ubuntu in Recovery Mode and use the option that fixes the Xorg or backup first the Xorg.conf.
If you can't manage to put it to work, you always have teh option to install Mint 7, a OS based in the Ubuntu 9.04 with compiz and all the stuff out of the box.

Hope that helps,
[/FONT]

---

### Post by kubanc on 2010-08-10
the [Waappu]("http://ubuntuforums.org/member.php?u=208041") 's solution is workin for ubuntu 10.04, but i disabled compiz
I'm using ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000]

Flash is working under fullscreen, but not HD.
Movies are also working under VLC, there is still some blurrines, but you need to look good if you would like to see it. I'm using Xvideo decoder

Thanks Waappu for the solutions

---

### Post by GABIKA6 on 2011-04-30
> **Waappu said:**
> Hi

You could try this

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_original
gksudo gedit /etc/X11/xorg.conf
```

File should be empty.

Paste these lines end of file
```
Section "Device"
    Identifier      "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
    Driver          "ati"
    # Hyödyllisiä kaikille ATI/AMD-korteille
    Option "AccelMethod" "EXA" # ilman tätä käytössä on ati-ajurilla toistaiseksi vanhempi XAA
    Option "DynamicClocks" "true" # virransäästöominaisuus joka ei ole oletuksena kytketty tällä hetkellä päälle
    # Seuraavat vain Mobility Radeon 9000 / 32MB näyttömuisti
    Option "FBTexPercent" "0" # oletus "50", "0" tarkoittaa että kaikki ylimääräinen muisti varataan EXA:lle. jos näyttömuistia on enemmän kuin 32MB, tätä ei kannattane käyttää.
    Option "GARTSize" "128" # AGP-muistin määrä, "128" voi olla tarpeen
    Option "AGPMode" "4" # AGP-nopeus, oletuksena usein "1". "4" varmistaa että AGP-siirtonopeus on riittävä kohtuullisen sulavaan Compizin käyttöön
    Option "DepthBits" "16" # vapauttaa lisää muistia muuhun käyttöön syvyyspuskurin kustannuksella, ei tunnu haittaavan peruskäytössä
    Option "AccelDFS" "true" # nopeuttaa 3D-työpöytää, joillain AGP-silloilla aiheuttaa ongelmia jonka takia oletus on "false"
    # Seuraava on luultavasti tarpeeton
    Option "EnablePageFlip" "true" # oletus "false", tuntuu toimivan ja teoriassa nopeuttaa jotain
 EndSection

```

log off and back in.

See if helps.

I take it from here and it did help on my friend laptop
[http://wiki.ubuntu-fi.org/3D-ty%C3%B6p%C3%B6yd%C3%A4n_nopeuden_optimointi_Radeon_Mobility_9000](http://wiki.ubuntu-fi.org/3D-ty%C3%B6p%C3%B6yd%C3%A4n_nopeuden_optimointi_Radeon_Mobility_9000)

Thanks a lot, it works fine. I used it on ubuntu 9.04, and the xorg.conf wasn't empty, but I replaced with your lines the device section, and worked fine. Thanks a lot.

---

