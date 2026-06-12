---
title: "after changeing to LCD screen, Beryl died on me..."
date: 2006-12-09
forum: Desktop Environments
---

### Post by zeltak on 2006-12-09
Hi all

I had beryl up and running great for about a month. Yesterday i changed to a LCD Asus screen (mw221u) with a resolution of 1680x1050 and now each time i either log in with my beryl session or run beryl-manager KDE kicks out to the graphic login screen. I do get the beryl wobbly logo and then back to the login screen. I am pretty new at Linux so i don't really know whats wrong. i am posting my Xorg.conf here below if it will help

Thx alot

Zeltak

Section "Files"
  # path to defoma fonts
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/100dpi:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
  FontPath "/usr/local/share/fonts"
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

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  option "MergedFB" "off"
EndSection

Section "Monitor"
  identifier "F910"
  vendorname "Generic"
  modelname "Flat Panel 1680x1050"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  gamma 1.0
EndSection

Section "Monitor"
  identifier "MW221U"
  HorizSync 47-84
  VertRefresh 56-76
  DisplaySize	474 296
  option	"DPMS"
EndSection


Section "Screen"
  Identifier "LCD"
  Device "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
  Monitor "MW221U"
  DefaultDepth 24
  DefaultFbBpp 32
  SubSection "Display"
    depth 24
    modes "1680x1050@60" "800x600@60" "640x480@60" 
    Virtual 1680 1050
  EndSubSection
  SubSection "Display"
    Depth 32
    Modes "1680x1050" "800x600"
    Virtual 1680 1050
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
#  screen 0 "Default Screen" 0 0
  Screen 0 "LCD" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 1
  option "MergedFB" "off"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

---

