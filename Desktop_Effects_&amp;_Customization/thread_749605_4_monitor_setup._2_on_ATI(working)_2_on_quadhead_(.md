---
title: "4 monitor setup. 2 on ATI(working) 2 on quadhead (mga driver, not working)"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by GoofYas007 on 2008-04-08
Hi,

I've tried gutsy & hardy to get the following to work but to no avail.

I've got a 4 monitor setup, placed in a row. All monitors are the same (eizo L565, LCD's 1280x1024)
the 2 right ones are setup on (as in connected to)  a ATI X800 card & working fine. I've got 2 screens (ie large desktop 2560 x 1024)
the 2 left ones are setup on (as in connected to) a quadhead G200 matrox card, normally using the MGA driver.
For some reason I can't get the 2 left monitors to work.
included the xorg.0.log.doc

If someone has a bright idea of what I'm missing I'm in eternal debt :-)   I'm kinda lost :confused:

PS in winXP I got it working so I know the G200 is working

lspci output
```
02:00.0 VGA compatible controller: ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)]
02:00.1 Display controller: ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)] (Secondary)
04:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)
04:04.0 Display controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)
04:08.0 Display controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)
04:0c.0 Display controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)
```

relevant xorg.conf setup
```
Section "Monitor"
        Identifier   "Monitor1"
        HorizSync    31.5 - 64.3
        VertRefresh  50.0 - 100.0
        #Option       "DPMS" "true"
EndSection

Section "Monitor"
        Identifier  "Monitor2"
        #Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier  "Monitor3"
        #Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier  "Monitor4"
        #Option      "DPMS" "true"
EndSection


Section "Device"
        Identifier  "X800-1"
        Driver      "fglrx"
        #Option      "DPMS"
        #VideoRam    65536
        Option      "DesktopSetup" "horizontal"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "X800-2"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
        Screen      1
EndSection

Section "Device"
        Identifier  "mga-1"
        Driver      "mga"
        #Option      "DPMS"
        #VideoRam    65536
        #Option      "DesktopSetup" "horizontal"
        BusID       "PCI:4:0:0"
EndSection

Section "Device"
        Identifier  "mga-2"
        Driver      "mga"
        #Option      "DPMS"
        #VideoRam    65536
        #Option      "DesktopSetup" "horizontal"
        BusID       "PCI:4:4:0"
EndSection

Section "Screen"
        Identifier "Screen 1"
        Device     "X800-1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen 2"
        Device     "X800-2"
        Monitor    "Monitor2"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


Section "Screen"
        Identifier "Screen 3"
        Device     "mga-1"
        Monitor    "Monitor3"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


Section "Screen"
        Identifier "Screen 4"
        Device     "mga-2"
        Monitor    "Monitor4"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Module"
	Load		"glx"

```

---

