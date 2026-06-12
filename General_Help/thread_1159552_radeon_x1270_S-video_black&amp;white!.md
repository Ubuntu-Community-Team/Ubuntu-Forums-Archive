---
title: "radeon x1270 S-video black&amp;white!"
date: 2009-05-14
forum: General Help
---

### Post by Jimmy Landby on 2009-05-14
So after countless of hours I got Ubuntu to recognize my TV. THOUGH it's now in black&white, and it's flickering quite some, which is annoying to say the least.

I know this is a common problem. Been searching around for a long time, without anything resulting in fixing my above issues. Used linux alot, years ago when it still used xf86 etc. So alot is quite uncommon to me, so any help is appreciated.

I'm using a Dell Latitude D531 (the older version with a sempron cpu, though I have 512mb more ram from another comp, so 1gb.)

My xorg.conf file looks silly with all the options, and I suppose the only real option I need is the atomtv one, if so, do tell me. Anyway; this is my xorg.conf file:

```

Section "Module"
    Load        "dri"
    Load        "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    Option        "DRI"            "true"
        Option "TVDACLoadDetect" "TRUE"
    Option "TVStandard" "PAL-B" 
    Option "TVOutFormat" "COMPOSITE"
    Option "ForceTVOut" "on" 
    Option      "TVFormat" "PAL-B"
    Option        "TVOutput" "PAL-B"
    Option "MonitorLayout" "TV,LFP"
    Option "Clone" "true"
    Option "ATOMTvOut" "TRUE"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Monitor"
    Identifier    "TV"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth     24
    SubSection "Display"
        Virtual 2080 800
        Modes       "1280x800" "800x600"
    EndSubSection
EndSection

```xrandr -q output:

```

Screen 0: minimum 320 x 200, current 800 x 600, maximum 2080 x 800
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3*    59.9  
   640x480        59.9     59.4  
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       59.9  
   800x600        60.3*    59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)

```Tried these commands, which gets the tv-out going, but with the obvious issues i've mentioned;

$ xrandr --addmode S-video 800x600
$ xrandr --output S-video --set load_detection 1
$ xrandr --output S-video --auto

then FN+F8.

$ xrandr --output S-video --set tv_standard pal

results in nothing, same with ntsc. I live in Sweden, so it's a PAL-B TV i'm using.

---

### Post by Jimmy Landby on 2009-05-14
I can add that i've tried changing PAL-B to PAL-G with no success.

---

### Post by Jimmy Landby on 2009-05-15
Bumping a little with some additional info; I'll add that I CANNOT use the fglrx catalyst driver. That driver gives me a very strange graphical error when I boot up with weird colors and just lines here and there, which makes it impossible to see what i'm doing.

---

### Post by Jimmy Landby on 2009-05-16
Seriously, noone has any clues? it'd be very appreciated.

---

