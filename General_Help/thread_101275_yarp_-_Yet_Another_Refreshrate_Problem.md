---
title: "yarp - Yet Another Refreshrate Problem"
date: 2005-12-09
forum: General Help
---

### Post by e2k on 2005-12-09
Hi.
I've been on Gentoo for about a year now, and thought I'd give Ubuntu a shot and see what it's all about. So far I'm very pleased, almost everything worked right out of the box. There is one thing I'm still struggling with though, the refreshrate.

I know there are several posts about this, but I can't find any answer to my particular problem.. The thing is, I can't manage to set my refreshrate to 75Hz@1280x1024. I've played around with xorg.conf for quite some time now without any results, I seem to be stuck with 60Hz. This is what it looks like:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
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
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fi"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "VP171s"
        HorizSync       30-82
        VertRefresh     50-85
        Option          "DPMS"
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
Modeline "1280x1024@75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
        Monitor         "VP171s"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection
```As you can see I've set the HorizSync and VertRefresh, without any results.. I also added the Modeline, but that too without any results, still going 60Hz, killing my eyes ;)

So what might this be? Any thoughts? :)

---

### Post by mo_x on 2005-12-09
For a LCD monitor the refresh rate is not so important as with a CRT monitor.
Your modeline is not in the modes list, you have to do something like:
Modes "1280x1024@75.00"

---

### Post by Appolusionist on 2005-12-09
[quote=e2k]Hi.
I've been on Gentoo for about a year now, and thought I'd give Ubuntu a shot and see what it's all about. So far I'm very pleased, almost everything worked right out of the box. There is one thing I'm still struggling with though, the refreshrate.
 
I know there are several posts about this, but I can't find any answer to my particular problem.. The thing is, I can't manage to set my refreshrate to 75Hz@1280x1024. I've played around with xorg.conf for quite some time now without any results, I seem to be stuck with 60Hz. This is what it looks like:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
 
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
 
Section "Module"
        Load    "GLcore"
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
EndSection
 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fi"
EndSection
 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
 
Section "Monitor"
        Identifier      "VP171s"
        HorizSync       30-82
        VertRefresh     50-85
        Option          "DPMS"
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
Modeline "1280x1024@75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection
 
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
        Monitor         "VP171s"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
        EndSubSection
EndSection
 
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
 
Section "DRI"
        Mode    0666
EndSection
```As you can see I've set the HorizSync and VertRefresh, without any results.. I also added the Modeline, but that too without any results, still going 60Hz, killing my eyes ;)
 
So what might this be? Any thoughts? :)[/quote]
 
I located your exact monitor and issue with google. Maybe this [link]("http://lists.freedesktop.org/archives/xorg/2005-October/010928.html") will point you in the right direction.

---

### Post by e2k on 2005-12-09
Thanks for the replies.. Appolusionist, I now recall having similiar problems when I installed gentoo, fortunately I had a nvidia card at that time, now I'm stuck with an Ati.. I'll try to update the driver and attempt to get fglrx working as the driver, I think that should fix it (I am using the DVI port, which seems to be the reason for this misbehaviour).

---

### Post by e2k on 2005-12-09
I installed the ati driver (fglrx, apparently I didn't have that one installed :shock:), edited xorg.conf and now it works! Thank you for your fast replies and help :)

---

