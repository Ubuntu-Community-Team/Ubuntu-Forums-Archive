---
title: "problem with mouse cursor on 2nd screen"
date: 2007-06-21
forum: Desktop Effects &amp; Customization
---

### Post by fadetoblack82 on 2007-06-21
ok so i have a laptop and an external monitor. i finally got the dual screen setup working with 1400x1050 on my primary laptop screen, and 1920x1200 on the 2ndary external monitor. everything works great, the only problem is that the mouse cursor on the secondary monitor is all screwed up. its just a square with those messed up diagonal lines. i tried playing around with the refresh rate on the 2ndary. here is my xorg.conf:

```

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
  screen 1 "screen1" rightof "aticonfig-Screen[0]"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "Synaptics Touchpad"
EndSection

Section "Files"
  # path to defoma fonts
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/usr/share/fonts/X11/misc"
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
  load "dbe"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
  option "XkbOptions" "altwin&"#58;super_win
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
  option "EmulateWheel" "true"
  option "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  option "DPMS"
EndSection

Section "Monitor"
  identifier "aticonfig-Monitor[0]"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "1400x1050@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Device"
  identifier "aticonfig-Device[0]"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "fglrx"
  screen 0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "aticonfig-Device[0]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    Depth 1
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 4
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 8
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 15
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 16
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
  SubSection "Display"
    Depth 24
    Modes "1024x768" "800x600" "640x480"
  EndSubSection
EndSection

Section "Screen"
  Identifier "aticonfig-Screen[0]"
  Device "aticonfig-Device[0]"
  Monitor "aticonfig-Monitor[0]"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1400x1050@60"
  EndSubSection
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  option "Composite" "0"
EndSection

Section "device" #  
  identifier "device1"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "fglrx"
  screen 1
EndSection

Section "screen" #  
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
  SubSection "Display"
    depth 24
    modes "1920x1200@60"
  EndSubSection
EndSection

Section "monitor" #  
  identifier "monitor1"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "1920x1200@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection
Section "ServerFlags"
  option "Xinerama" "true"
EndSection
Section "device" # 
  identifier "device2"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "fglrx"
  screen 2
EndSection
Section "screen" # 
  identifier "screen2"
  device "device2"
  defaultdepth 24
  monitor "monitor2"
EndSection
Section "monitor" # 
  identifier "monitor2"
  gamma 1.0
EndSection


```

---

### Post by aro_ron_chynn on 2007-06-21
I am having this exact same problem. Very annoying. Any help would be great.

---

### Post by fadetoblack82 on 2007-06-21
> **aro_ron_chynn said:**
> I am having this exact same problem. Very annoying. Any help would be great.

what resolutions are you running? apparently when i run the same res on the 2nd monitor (1400x1050) then the cursor is fine - only happens when the res is higher than the 1st.

---

### Post by aro_ron_chynn on 2007-06-21
both monitors have the exact same resolution and refresh rates.

I am still new to linux in general, but have been playing and learning with Ubuntu since 6.06 came out. Back then, dual head worked perfectly for me, as well as proprietary ATI drivers let it work. Even when I upgraded to 6.10, still worked fine. but 7.04 just keep giving me problems with stuff that used to be simple to set up.

Most of it I have worked out now, but the mouse is still a problem. Any help would be hot!

---

### Post by fadetoblack82 on 2007-06-21
so it worked fine for you in 6.10? because im running 6.10 and still having that problem

---

### Post by aro_ron_chynn on 2007-06-21
Well, now that I think about it... I was away at College when 6.10 was released... and didnt have dual head set up due to desk size... so I never tested it...And 7.04 came out before I got back home....

Darn it all... it all runs together....

---

### Post by fadetoblack82 on 2007-06-21
bump

---

### Post by fadetoblack82 on 2007-06-22
> **aro_ron_chynn said:**
> Well, now that I think about it... I was away at College when 6.10 was released... and didnt have dual head set up due to desk size... so I never tested it...And 7.04 came out before I got back home....

Darn it all... it all runs together....

see thread:

[http://ubuntuforums.org/showthread.php?t=227902](http://ubuntuforums.org/showthread.php?t=227902)

more people w/ the same problem

---

