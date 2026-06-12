---
title: "Intel 855gm and second Monitor or TV?!"
date: 2005-12-29
forum: Desktop Environments
---

### Post by gogi on 2005-12-29
Hello All!

I'm working on my Intel 855gm graphic-card and nothing goes! I don't know what else i can do. I've read every kind about it but can't get my second monitor working or the tv.

I would be glad if somebody would find some failure in my xorg.conf:
```

#Devices

Section "Device"
   Identifier   "Device[0]"
   Driver      "i810"
   BusID      "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "Device[1]"
        Driver          "i810"
        Screen          0
        BusID           "PCI:0:2:0"
   Option      "MonitorLayout"   "CRT,LFP"
EndSection

Section "Device"
   Identifier   "Device[2]"
   Driver      "i810"
   Screen      1
   BusID      "PCI:0:2:0"
   Option      "MonitorLayout"   "CRT,LFP"
        Option          "Clone"         "true"
   Option      "CloneRefresh"   "85"
EndSection

Section "Device"
   Identifier   "Device[3]"
   Driver      "i810"
   Screen      0
   BusID      "PCI:0:2:0"
   Option      "MonitorLayout"   "TV,LFP"
EndSection

Section "Device"
   Identifier   "Device[4]"
   Driver      "i810"
   Screen      1
   BusID      "PCI:0:2:0"
   Option      "MonitorLayout" "TV,LFP"
        Option          "Clone"         "true"
   Option      "CloneRefresh"   "25"
EndSection

#Monitors

Section "Monitor"
   Identifier   "Monitor[0]"
   Option      "DPMS"
EndSection

Section "Monitor"
   Identifier   "Monitor[1]"
   Option      "DPMS"
EndSection

Section "Monitor"
   Identifier   "Monitor[2]"
   Option      "DPMS"
EndSection

#Screens

Section "Screen"
   Identifier   "Screen[0]"
   Device      "Device[0]"
   Monitor      "Monitor[0]"
   DefaultDepth   24
   SubSection "Display"
      Depth      24
      Modes      "1400x1050"
   EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen[1]"
        Device          "Device[1]"
        Monitor         "Monitor[0]"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
      Modes      "1400x1050"
        EndSubSection
EndSection

Section "Screen"
   Identifier   "Screen[2]"
   Device      "Device[2]"
   Monitor      "Monitor[1]"
   DefaultDepth   24
   SubSection "Display"
      Depth      24
      Modes      "1280x1024"
      Virtual      1400 1050
   EndSubSection
EndSection

Section "Screen"
   Identifier   "Screen[3]"
   Device      "Device[3]"
   Monitor      "Monitor[0]"
   DefaultDepth   24
   SubSection "Display"
      Depth      24
      Modes      "1400x1050"
   EndSubSection
EndSection

Section "Screen"
   Identifier   "Screen[4]"
   Device      "Device[4]"
   Monitor      "Monitor[2]"
   DefaultDepth    24
   SubSection "Display"
      Depth      24
   EndSubSection
EndSection

#ServerLayouts

Section "ServerLayout"
   Identifier   "Default Layout"
   Screen      0 "Screen[0]" 0 0
   InputDevice   "InputDevice[0]"
   InputDevice   "InputDevice[1]"
   InputDevice   "InputDevice[2]"
EndSection

Section "ServerLayout"
        Identifier      "ServerLayout[1]"
        Screen          0 "Screen[1]" 0 0
        Screen          1 "Screen[2]" RightOf "Screen[1]"
        InputDevice     "InputDevice[0]"
        InputDevice     "InputDevice[1]"
        InputDevice     "InputDevice[2]"
EndSection

Section "ServerLayout"
   Identifier   "ServerLayout[2]"
   Screen      0 "Screen[3]" 0 0
   Screen      1 "Screen[4]" RightOf "Screen[3]"
   InputDevice   "InputDevice[0]"
   InputDevice   "InputDevice[1]"
   InputDevice   "InputDevice[2]"
EndSection

```

Thank you!

---

