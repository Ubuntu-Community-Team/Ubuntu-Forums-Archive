---
title: "Dell 1907FP Monitor behaviour is weird"
date: 2007-09-27
forum: Dell  Ubuntu Support
---

### Post by dianep on 2007-09-27
Hi there,

I am running ubuntu on a cobbled-together system. The monitor is
a DELL 1907FP which is pretty new and replaced my very old monitor (don't remember what that was).  I have the resolution set okay but 
the weird thing is that when I run a computationally intensive program
(I'm mostly running fortran and idl programs) the screen jiggles side
to side a small amount. Has anyone seen this before?

Here are a few more details:
Video card:Radeon RV100 QY [Radeon 7000/VE] from ATI 
In xorg.conf:

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL 1907FP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
        Monitor         "DELL 1907FP"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Any ideas?
Thanks,
diane

---

