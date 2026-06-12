---
title: "Radeon 9600 M10 e DRI"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by maddom on 2007-08-31
Hello everibody,
i installed ubuntu 7.04 on my laptop recently and i think it's a very nice distro. Now i'm trying to enable DRI for my ati radeon 9600 M10 but after log in gdm x fails to start, the screen is black and i can only move the mouse; if i do failsafe terminal and write glxinfo everything seems good (Dri is enabled, glx vendor is SGI...). When i put # before Load dri in xorg.conf gdm starts, but i I do not have more DRI obviously. I'm becoming crazy. 
However this is my xorg.conf :

Section "Files"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
Load "v4l"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
Driver "radeon"
BusID "PCI:1:0:0"
Option "XAANoOffscreenPixmaps"
Option "DRI" "true"
EndSection

Section "Monitor"
Identifier "LCD"
Option "DPMS"
HorizSync 28-50
VertRefresh 43-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
Monitor "LCD"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
Option "AIGLX" "true"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

This is my :0.log.4 su /var/log/gdm:

(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 11 21:37:09 2006
(EE) Unable to locate/open config file
xf86PciVideoInfo is not set
(==) Using default built-in configuration (43 lines)
(EE) open /dev/fb0: No such file or directory

Fatal server error:
A driver tried to allocate the Block Memresource at
0xa0000:0xaffff which conflicted with another resource. Send the
output of the server to [email]xorg@lists.freedesktop.org[/email]. Please
specify your computer hardware as closely as possible.

And this is the link for my Xorg.0.log: [http://www.freefilehosting.net/download/MTY4Nzk=](http://www.freefilehosting.net/download/MTY4Nzk=)

Help me, please!

---

### Post by maddom on 2007-08-31
Is it possible that nobody can help me?

---

### Post by cudaman73 on 2007-08-31
Did you submit your Xorg.0.log to the Xorg devs? that's really the only thing I can contribute to the situation.

I've never encountered any error like that, and I'm not an ATi user, so I don't know too much about that.

I wish I could help more.

---

