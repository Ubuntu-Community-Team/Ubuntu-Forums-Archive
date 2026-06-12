---
title: "Kwin/X confused about screen resolution after turning second monitor off w. twinview"
date: 2010-01-14
forum: Desktop Environments
---

### Post by janjan7777 on 2010-01-14
Dear all,
When using my laptop (1680x1050) at work, I connect it to an external monitor (1280x1024) and extend the desktop to span both screens using twinview, which works perfectly. Now, when I go home, I turn off the external monitor in nvidia-settings so that I can suspend the laptop and continue using my session at home.

The problem is that now window placement still assumes the big resolution of the 2-screen-setup. For example, the application launcher is not centred in the screen, but slightly off screen (as would be the center position with the other screen enabled), and, much worse, the panel might disappear (seams that it is positioned off-screen). This gets even worse when I play with screen rotation in nvidia-settings (giving me an y-resolution of 1280 or even 1680 pixels). This means that I have to restart X to get everything properly working.

My impression is the decreasing the screen resolution leaves some internally stored values of X/kwin at the wrong values. Has anybody seen a similar behaviour or even a solution to reset this internal values to the correct resolution without having to restart X?

Thank you very much,
Jan

My setup:
Laptop: Dell Precision M65 with NVidia QuadroTM FX Go350M
Ext. monitor: IIyama ProLite E481S
System: Kubuntu 9.10/Karmic, KDE4
Nvidia proprietary drivers, Version 185

xorg.conf
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"    
EndSection                                   

Section "Files"
EndSection     

Section "ServerFlags"
    Option         "HandleSpecialKeys" "Always"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "CoolBits" "1"
    Option         "AllowGLXWithComposite" "True"
    Option         "RandRRotation" "True"
    Option         "DamageEvents" "True"
    Option         "ConstantDPI" "True"
    Option         "DynamicTwinView" "True"
    Option         "IncludeImplicitMetaModes" "True"
    Option         "Rotate" "NORMAL"
    Option         "TwinViewOrientation" "RightOf"
    Option         "ModeValidation" "CRT-0: NoHorizSyncCheck, NoVertRefreshCheck"
#    Option         "ModeValidation" "DFP-0: AllowNon60HzDFPModes,NoHorizSyncCheck ; CRT-0: NoHorizSyncCheck, NoVertRefreshCheck"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Xorg.0.log after extending/shrinking:
s. Attachment

first lines of xdpyinfo:
```

name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10604000
X.Org version: 1.6.4
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x400001d, revert to PointerRoot
number of extensions:    30
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    DRI2
    GLX
    Generic Event Extension
    MIT-SCREEN-SAVER
    MIT-SHM
    NV-CONTROL
    NV-GLX
    RANDR
    RECORD
    RENDER
    SECURITY
    SHAPE
    SYNC
    X-Resource
    XC-MISC
    XFIXES
    XFree86-DGA
    XFree86-VidModeExtension
    XINERAMA
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    XVideo-MotionCompensation
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1680x1050 pixels (330x211 millimeters)
  resolution:    129x126 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x237
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfac031
    KeyPressMask             EnterWindowMask          LeaveWindowMask
    KeymapStateMask          ExposureMask             StructureNotifyMask
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask
    PropertyChangeMask       ColormapChangeMask
  number of visuals:    192
  default visual id:  0x21
  visual:
    visual id:    0x21
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    10 bits
...
```Packages:
```
$ dpkg -l nvidia\* | grep ^ii
ii  nvidia-173-modaliases                                  173.14.20-0ubuntu5                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-185-kernel-source                               185.18.36-0ubuntu9                         NVIDIA binary kernel module source
ii  nvidia-185-libvdpau                                    185.18.36-0ubuntu9                         Video Decode and Presentation API for Unix
ii  nvidia-185-modaliases                                  185.18.36-0ubuntu9                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                                   96.43.13-0ubuntu6                          Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                                          0.2.15.1                                   Find obsolete NVIDIA drivers
ii  nvidia-glx-185                                         185.18.36-0ubuntu9                         NVIDIA binary Xorg driver
ii  nvidia-settings                                        180.25-0ubuntu1                            Tool of configuring the NVIDIA graphics driv
```

---

