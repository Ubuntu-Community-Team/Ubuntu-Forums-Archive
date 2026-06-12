---
title: "Xinerama's acting weird?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by JasonValdron on 2006-08-08
Hi there,
I've setted up a xinerama. But, when I run kdm back, I see my backgrounds all fine, but I don't have any desktop icons, panels, window, anything! If I disable my second screen removing the line (Screen "S3 Screen" LeftOf "Default Screen"), everything's fine! Here is my config file:
> Section "Extensions"
  option "Composite" "Enable"
EndSection

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
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
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

# Start of NVIDIA PCI-E
Section "Device"
  identifier "NVIDIA PCI-E"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  Option "AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Dell"
  modelname "Dell 1702FP (Digital)"
  HorizSync 30.0-80.0
  VertRefresh 56.0-76.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA PCI-E"
  Monitor "Generic Monitor"
  DefaultDepth 24
  Subsection "Display"
    Depth       24
    Modes "1280x1024" "1024x768" "800x600" "640x480"
    ViewPort    0 0
  EndSubsection
EndSection

# Start of S3 Virge
Section "Device"
  identifier "S3 ViRGE PCI"
  boardname "S3 ViRGE (generic)"
  busid "PCI:5:6:0"
  driver "s3virge"
EndSection

Section "Monitor"
  identifier "DataTrain Monitor"
  vendorname "DataTrain"
  modelname "DataTrain DC529"
  HorizSync 30.0-80.0
  VertRefresh 56.0-76.0
EndSection

Section "Screen"
  Identifier "S3 Screen"
  Device "S3 ViRGE PCI"
  Monitor "DataTrain Monitor"
  DefaultDepth 24
  Subsection "Display"
    Depth       24
    Modes "1024x768" "800x600" "640x480"
    ViewPort    0 0
  EndSubsection
EndSection

Section "ServerFlags"
  Option "Xinerama" "true"
EndSection

Section "ServerLayout"
    Identifier  "Simple Layout"
    Screen "Default Screen"
    Screen "S3 Screen" LeftOf "Default Screen"
    InputDevice "Configured Mouse" "CorePointer"
    InputDevice "Generic Keyboard" "CoreKeyboard"
EndSection

Section "DRI"
  Mode 0666
EndSection

Can someone help me? Thanks!

---

### Post by JasonValdron on 2006-08-08
Arhh... bump

---

