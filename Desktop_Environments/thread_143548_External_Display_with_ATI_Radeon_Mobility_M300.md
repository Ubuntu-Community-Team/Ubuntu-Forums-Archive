---
title: "External Display with ATI Radeon Mobility M300"
date: 2006-03-12
forum: Desktop Environments
---

### Post by coachher on 2006-03-12
Hi,

 I'm running badger on a laptop and I've been trying to set up my xorg.conf file for a while without a lot of luck. I'm using the  open source "radeon" driver. The primary display (the laptop screen) works fine, but I can't get the external display working perfectly. 

Essentially, I have two different situations that I want to be able to handle. 
1. Plugging in an external monitor: My default resolution is 1400x1050 which the monitor can support. When I plug in the monitor the display should be at 1400x1050. Ideally, I'd also like to be able to choose whether to clone the laptop screen to the external monitor or whether to merge the two into a larger display.

I've tried a couple of different things like changing the driver options and setting up a second Screen section, but what ever I try, I always get some clipping. The left side of the screen is cut off and not visible.

2. Plugging into a projector: The problem with projectors is that they don't support such high resolutions. So I get a funny white overlay on the picture that is projected. What I'd like to be able to do is change the resolution for the external device if I've plugged in to a projector (I can do this manually).

This is what the Device, Monitor and Screen sections of my xorg.conf file look like right now. Any help would be really appreciated. Thanks.
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "MonitorLayout"         "LVDS"
#        Option          "MonoitorLayout"       "LVDS, CRT"
        Option          "backingstore"          "true"
        Option          "DynamicClocks"         "true"
#        Option          "MergedFB"                              "true"
#        Option          "CRT2Position"          "LeftOf"
#        Option          "OverlayOnCRTC2"        "on"
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     50-75
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     50-72
EndSection

Section "Screen"
        Identifier      "LCD Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768" "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "LCD Screen"
        Screen          "External Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad" "AlwaysCore"
EndSection
```

---

### Post by tperica on 2006-04-11
hi i have exact the same problem !
i am new to Linux and ubunutu, after 12 y as sys admin for Win platform, i have decided to go completely with Linux.

ThinkPad 43
"ATI Technologies, Inc. Radeon Mobility M300 (M22)"

cheers
tomislav

---

