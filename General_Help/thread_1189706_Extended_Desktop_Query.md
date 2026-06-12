---
title: "Extended Desktop Query"
date: 2009-06-17
forum: General Help
---

### Post by coolboarderguy on 2009-06-17
Hi All,

I'm trying to follow here,

[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

and below is my xorg.conf output. I now see both screens in Screen Resolution Preferences but I get the below on the 2nd monitor,

Not Optimum Mode
Recommended Mode : 1680x1050 60Hz.

Do I perhaps need to add more Depths under SubSection Display?

Section "Device"
        Identifier      "0 ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          0
        Option "DDCMode" "True"
        Option "MonitorLayout" "LVDS,LVDS"
EndSection

Section "Device"
        Identifier      "1 ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Screen          1
        Option "DDCMode" "True"
        Option "MonitorLayout" "LVDS,LVDS"
EndSection

Section "Monitor"
        Identifier      "Main Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60

EndSection

Section "Monitor"
        Identifier      "Second Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60

EndSection


Section "Screen"
        Identifier      "Main Screen"
        Device          "0 ATI Technologies, Inc. ATI Default Card"
        Monitor         "Main Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "1 ATI Technologies, Inc. ATI Default Card"
        Monitor         "Second Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen      0   "Main Screen"
        Screen      1   "Second Screen" RightOf "Main Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by ezramorris on 2009-06-17
What version of Ubuntu are you running?

---

### Post by coolboarderguy on 2009-06-17
Feisty...yeah, I know, bit old...why?

---

### Post by ezramorris on 2009-06-17
> **coolboarderguy said:**
> Feisty...yeah, I know, bit old...why?

Because from my experience, in Jaunty, I haven't had to edit any config files for extended desktop; everything is detected automatically in System>Preferences>Display.

---

### Post by coolboarderguy on 2010-06-22
Bumping this one back up....have finally got around to installing a newer version of Ubuntu (10.04 LTS). I have dual monitors (Laptop and Samsung SyncMaster 2243bw) but the 2243 looks horrible. Very fuzzy and jittery. Settings are below. Drivers perhaps?

1680 x 1050 (16:10)
60Hz
Normal

---

### Post by coolboarderguy on 2010-06-22
Looks like it could be related to the below. Will test tonight and report back my results. Thanks.

[http://ubuntuforums.org/showthread.php?t=1467220](http://ubuntuforums.org/showthread.php?t=1467220)

---

### Post by coolboarderguy on 2010-06-23
Fix in the above link worked a treat. Thanks

---

