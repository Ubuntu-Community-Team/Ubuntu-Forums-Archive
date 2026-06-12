---
title: "resolution"
date: 2006-05-25
forum: Desktop Environments
---

### Post by amunimanghi on 2006-05-25
Hi,

I was wondering if I can change the resolution to a different resolution not in the screen resolution manager. (see the attached picture) also, what is the Hz drop-down menu mean?

---

### Post by 23meg on 2006-05-25
You can; check out [this guide]("http://www.ubuntuforums.org/showthread.php?t=83973"). The Hertz value is the refresh rate of your screen, which means how many times a second it redraws the image displayed.

---

### Post by richbarna on 2006-05-25
Hi amunimanghi,
The hz drop down is the refresh rate (mine is set to 60).
To change the resolution on the xserver you can do one of two things.
1. Click Ctrl, Alt, + or - to scroll through your available resolutions.
2. Edit your Xorg Configuration file.

> sudo gedit /etc/X11/xorg.conf
And then choose your preferred resolution settings

> Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        **DefaultDepth    24**
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection


---

### Post by amunimanghi on 2006-05-26
Thanks everyone. Okay, now to the problem I added ```
[B]
DefaultDepth 24[/B]    
 SubSection "Display"
Depth 24
Modes **"1024x1024" **"1024x768" "832x624" "800x600" "640x480"
EndSubSection
EndSection
```

How would I activate it? Also, is it better if my Hz rate is higher or lower?

---

