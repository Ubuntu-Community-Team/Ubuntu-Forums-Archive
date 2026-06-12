---
title: "KDE picks its own resolutions--make it stop!"
date: 2006-09-10
forum: Desktop Environments
---

### Post by ac4000 on 2006-09-10
[Note:  I've simplified the problem and reposted [here]("http://www.ubuntuforums.org/showthread.php?t=259718").]

I have a projector, which I sometimes use, and a main desktop LCD monitor.  Each has an ideal resolution and refresh rate, so I've restricted my xorg.conf file to those settings.  Thing is, when I get to my session, and run System Settings --> Display, it has a) usually picked another resolution or my second display (e.g., 800x600, rather than 1280x960), and b) it offers me choices of refresh rates and resolutions that it should not (based on my xorg.conf settings).  My xorg.conf is below....  Any ideas?

To reiterate:

My xorg.conf file is not restricting the session to listed modes for a given screen layout.

Also, if anyone has any thoughts, the following related issues would be nice to resolve:

1.  A way to switch screen layouts from KDM--but I think it has already loaded them by that point.  I suppose I could just start in console and pick that way.

2.  A way to have the card actually not send a signal (cloned or otherwise) when I'm using a screen layout without the projector.

Thanks in advance for your thoughts and help!

```

# LAYOUT
Section "ServerLayout"
        Identifier      "Projector On"
        Screen          "Desktop Screen"
        Screen          "Projector Screen" Above "Desktop Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "ServerLayout"
        Identifier      "Test Screen On"
        Screen          "Desktop Screen"
        Screen          "Test Screen" Above "Desktop Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "ServerLayout"
        Identifier      "Projector Off"
        Screen          "Desktop Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


# VIDEO CARD HEADS
Section "Device"
        Identifier      "ATI R350 NH [Radeon 9800 Pro] (Primary)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "ATI R350 NH [Radeon 9800 Pro] (Secondary)"
        Driver          "fglrx"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
        Option          "OverlayOnCRTC2" "1"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection


# MONITORS
Section "Monitor"
        Identifier      "Princeton SENergy 714"
        VendorName      "Princeton"
        ModelName       "SENergy 714"
        Option          "DPMS"
        HorizSync       24-82
        VertRefresh     55-77
        DisplaySize     337 270
        # Recommended
        Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076
        # Maximum
        Modeline "1280x1024@69" 140.00 1280 1312 1840 1872 1024 1044 1056 1076
EndSection

Section "Monitor"
        Identifier      "Sony VPH-1272Q"
        VendorName      "Sony"
        ModelName       "VPH-1272Q"
        HorizSync       15-93
        VertRefresh     38-150
        DisplaySize     2032 1524
        # Modeline Generator Used:  http://xtiming.sourceforge.net/cgi-bin/xtiming.pl
        # DVD FORMATS; 720p is 1280x720, so the appropriate 4:3 is 1280x960
          # Film x1 (24 fps); V-freq: 24.00 Hz  // h-freq: 23.38 KHz
            # BELOW 38Hz minimum; Modeline "1280x960@24" 35.84 1280 1312 1448 1480 960 982 986 1009
          # Film x2 (48 fps); V-freq: 48.00 Hz  // h-freq: 47.45 KHz
            Modeline "1280x960@48" 79.77 1280 1312 1608 1640 960 980 988 1009
          # Film x3 (72 fps); V-freq: 72.00 Hz  // h-freq: 72.24 KHz
            # ABOVE 85Mhz dot clock; Modeline "1280x960@72" 134.87 1280 1312 1824 1856 960 979 990 1009
          # NTSC (29.97 fps); V-freq: 29.97 Hz  // h-freq: 29.30 KHz
            # BELOW 38Hz minimum; Modeline "1280x960@30" 45.92 1280 1312 1480 1512 960 982 987 1009
          # PAL (25 fps); V-freq: 25.00 Hz  // h-freq: 24.37 KHz
            # BELOW 38Hz minimum; Modeline "1280x960@25" 37.50 1280 1312 1448 1480 960 982 986 1009
          # Computer (typical); V-freq: 60.00 Hz  // h-freq: 59.75 KHz
            # ABOVE 85Mhz dot clock; Modeline "1280x960@60" 105.68 1280 1312 1712 1744 960 979 989 1009
          # Maximum refresh at this resolution (based on 85Mhz dot clock).
            Modeline "1280x960@50" 85.00 1280 1312 1632 1664 960 980 988 1009
EndSection

Section "Monitor"
        Identifier      "Mitsubishi DiamondPoint M55 LCD"
        VendorName      "Mitsubishi"
        ModelName       "DiamondPoint M55 LCD"
        Option          "DPMS"
        # Maximum
        Modeline "1024x768@72" 81.13 1024 1056 1360 1392 768 783 792 807
EndSection


# SCREENS
Section "Screen"
        Identifier      "Desktop Screen"
        Device          "ATI R350 NH [Radeon 9800 Pro] (Primary)"
        Monitor         "Princeton SENergy 714"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024@60"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Projector Screen"
        Device          "ATI R350 NH [Radeon 9800 Pro] (Secondary)"
        Monitor         "Sony VPH-1272Q"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x960@48"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Test Screen"
        Device          "ATI R350 NH [Radeon 9800 Pro] (Secondary)"
        Monitor         "Mitsubishi DiamondPoint M55 LCD"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768@72"
        EndSubSection
EndSection


# FILES
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection


# MODULES
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


# INPUT
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

# DRI
Section "DRI"
        Mode    0666
EndSection

```

---

