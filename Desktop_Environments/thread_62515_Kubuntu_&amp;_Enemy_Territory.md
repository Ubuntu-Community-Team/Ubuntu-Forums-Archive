---
title: "Kubuntu &amp; Enemy Territory"
date: 2005-09-04
forum: Desktop Environments
---

### Post by metlock on 2005-09-04
Howdy, just started with Kubuntu and already like it better than Ubuntu/Gnome...however, I'm having problems with Enemy Territory. The program starts up, gets going with sound, video appears fine, but it runs slow...very slow.

What should I do next to trouble-shoot this (or help you trouble-shoot)?

Thanks in advance...don't know if this is helpful but here's my xorg.conf excerpt:

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-85
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"

---

### Post by ltmon on 2005-09-05
I think you might be out of luck.

If you aren't running a Nvidia or ATI based graphics card you can't get opengl hardware acceleration working.  These are the only two companies who have released Linux drivers.

The drivers for your Intel card are written by open source developers, but without the specs from Intel (and probably a whole lot of time and effort) they can't produce effective hardware acceleration.

Solution: You should get an el-cheapo nvidia (geforce-4 or something) off ebay or something like that to get fancy graphics under Linux.

Cheers,

L.

---

### Post by Mishura on 2005-09-05
Those el-cheapos will run ET ok.  I've played ET with a Geforce2 MX 200 or so and I was able to play OK.  Make sure its AGP.

---

