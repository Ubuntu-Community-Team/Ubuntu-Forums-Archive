---
title: "X Server Composite Extension"
date: 2008-06-20
forum: Desktop Environments
---

### Post by Kelan on 2008-06-20
Hi everyone,

I've recently set up my X server to use dual monitors, and this seems to work fine -- however, I've noticed that I can no longer use the "composite" extension. The likes of Compiz and Kompmgr complain that this extension cannot be found / is disabled, even though I have (what I think is) the appropriate line to enable it in my xorg.conf:

```

Section "Files"

  Fontpath "/usr/local/share/fonts"

EndSection

Section "InputDevice"

  Identifier  "Generic Keyboard"
  Driver      "kbd"
  Option      "CoreKeyboard"
  Option      "XkbRules"    "xorg"
  Option      "XkbModel"    "pc105"
  Option      "XkbLayout"   "us"
  Option      "XkbVariant"  "dvorak"
  Option      "XkbOptions"  "lv3:ralt_switch"

EndSection

Section "InputDevice"

  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device"           "/dev/input/mice"
  Option      "Protocol"         "ImPS/2"
  Option      "ZAxisMapping"     "4 5"
  Option      "Emulate3Buttons"  "true"

EndSection

Section "Extensions"

  Option "Composite" "Enable"

EndSection

Section "Device"

  Identifier "NVIDIA GeForce 8600 GT:0"
  BoardName  "GeForce 8600 GT"
  Driver     "nvidia"
  VendorName "NVIDIA Corporation"

  Busid      "PCI:2:0:0"
  Option     "RenderAccel"       "True"
  Option     "AddARGBVisuals"    "True"
  Option     "AddARGBGLXVisuals" "True"
# Option     "NoLogo"            "True"

  Screen      0

EndSection

Section "Device"

  Identifier "NVIDIA GeForce 8600 GT:1"
  BoardName  "GeForce 8600 GT"
  Driver     "nvidia"
  VendorName "NVIDIA Corporation"

  Busid      "PCI:2:0:0"
  Option     "RenderAccel"       "True"
  Option     "AddARGBVisuals"    "True"
  Option     "AddARGBGLXVisuals" "True"
# Option     "NoLogo"            "True"

  Screen      1

EndSection

Section "Monitor"

  Identifier   "AOC Monitor"
  VendorName   "Unknown"
  ModelName    "AOC 210V"
  HorizSync     31.0 - 80.0
  VertRefresh   56.0 - 75.0

EndSection

Section "Monitor"

  Identifier  "TVM Monitor"
  VendorName  "Unknown"
  ModelName   "TVM"
  HorizSync    31.5 - 60.0
  VertRefresh  56.0 - 75.0

EndSection

Section "Screen"

  Identifier   "Left Screen"
  Device       "NVIDIA GeForce 8600 GT:0"
  Monitor      "AOC Monitor"
  Defaultdepth  24

  Option       "TwinView"  "0"
  Option       "metamodes" "DFP: nvidia-auto-select +0+0"

EndSection

Section "Screen"

  Identifier   "Right Screen"
  Device       "NVIDIA GeForce 8600 GT:1"
  Monitor      "TVM Monitor"
  Defaultdepth  24

  Option       "TwinView"  "0"
  Option       "metamodes" "DFP: nvidia-auto-select +0+0"

EndSection

Section "ServerFlags"

  Option "Xinerama" "True"

EndSection

Section "ServerLayout"

  Identifier  "Default Layout"
  Screen    0 "Left Screen" 0 0
  Screen    1 "Right Screen" RightOf "Left Screen"
  Inputdevice "Generic Keyboard"
  Inputdevice "Configured Mouse"

EndSection

Section "Module"

  Load "glx"
  Load "freetype"

EndSection

```

As you can see from the above, I'm using a NVIDIA GeForce 8600 GT card, and also (K)Ubuntu 8.04. Each of my monitors is configured as a separate X screen.

If anyone has any thoughts on this, I'd be very grateful to hear them. ^^

Long days and pleasant nights,
-- Kelan

---

