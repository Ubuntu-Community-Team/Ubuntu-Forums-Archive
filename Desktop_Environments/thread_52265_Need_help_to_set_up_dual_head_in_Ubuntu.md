---
title: "Need help to set up dual head in Ubuntu"
date: 2005-07-27
forum: Desktop Environments
---

### Post by cornelis on 2005-07-27
hi all,

Can any gurus here help me set up my ubuntu for dual head. My aim is to get each monitor to be separate desktop automatically after login.

I managed to do dual head but it consider the 2 monitors to be single desktop using xinerama. I tried to off the xinerama option, and this make it worse since i cannot start my X window. 


here is my xorg.conf

Section "ServerLayout"
Identifier "Multihead Layout"
Screen "Default Screen" LeftOf "Screen 2" 
Screen "Screen 2"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
Option "Xinerama" "on"
Option "Clone" "off"
EndSection

Section "Files"

# local font server
# if the local font server has problems, we can fall back on these
# paths to defoma fonts
FontPath "unix/:7100"
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Monitor"

### Uncomment if you don't want to default to DDC:
HorizSync 24.0 - 82.0
VertRefresh 50.0 - 85.0
Identifier "LCD 19"
Option "DPMS"
EndSection

Section "Monitor"

### Uncomment if you don't want to default to DDC:
HorizSync 30.0 - 80.0
VertRefresh 50.0 - 85.0
Identifier "LCD 17"
Option "DPMS"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 7200 (R100 QD)"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PP/PRO (TMDS Xpert 128)"
Driver "ati"
BusID "PCI:0:11:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 7200 (R100 QD)"
Monitor "LCD 19"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen 2"
Device "ATI Technologies, Inc. Rage 128 PP/PRO (TMDS Xpert 128)"
Monitor "LCD 17"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection


thanks

---

### Post by Shiven on 2005-07-27
disable xinerama if you don't want one big desktop across two screens...

have a look at this, its pretty universal: [http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

hopefully that will help

---

