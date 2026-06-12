---
title: "configure xorg for best results"
date: 2007-07-27
forum: Desktop Environments
---

### Post by mailmaldi on 2007-07-27
so I have a intel 915 motherboard & after much trials and tribulations i can still not get xorg to configure perfectly.
When i enable compiz/ beryl , i still cant play videos ( only audio comes out while video is blackened)

so far i installed xserver-xorg-video-intel & removed the i810

reconfigured xserver-xorg & my current xorg.conf is

```
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-71
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Some other threads have people saying try adding 

dbe to "Module"
 and
Section "Extensions"
	Option	"Composite"		"true"
EndSection
and 

Option		"XAANoOffscreenPixmaps"	"true"
in the device section.

can someone explain what do all these settings do actually?

---

### Post by Richard Kut on 2007-07-27
Hi mailmaldi. To your settings questions, the dbe module stands for Double Buffer Extension. This is supposed to give smoother animation and video playback. The composite option will allow a composite window manager like compiz to display shadows and transparency. Just remember that nothing is free, so enabling these options may slow your video response time.

Typing "man xorg.conf" in a terminal provided this info about XAANoOffscreenPixmaps: "disables accelerated draws into pixmaps stored in off-screen video memory".

Note that a fellow forum member has written a gui tool to edit the xorg.conf file, and maybe using this tool would help you. If you are interested, then have a look here:

[http://ubuntuforums.org/showthread.php?t=156243]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback")

Finally, regarding the black window during video playback, have a look here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback)

Note that there are some other good tips for your intel 915 card on the above site.

I hope that some of the above helps. Please update this post with your progress and comments.

Good luck!

---

