---
title: "Screen off-center to the right in 7.04"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Eshu on 2007-04-21
I did a new install of 7.04 on a seperate partition and my screen is ~10 pixels off to the right. I had the same problem when I set up 6.10 and adjusted it via a Modeline correction. I tried copying the xorg.conf file over from 6.10 to see if that would fix the problem but it didn't. (IIRC, it caused X/GDE to crash.) Unfortunately I'm not at home currently so no access to my conf file. Anyone have hints or suggestions how I might be able to fix it?

Thanks in advance.

---

### Post by meng on 2007-04-21
Have you tried adjusting the horizontal shift on your monitor?

---

### Post by Eshu on 2007-04-21
I have a KVM switch and would rather not have to readjust the monitor every time I switch computers. I was able to get the display 'fixed' in 6.10. Guess I'll mess with it later to see if I can figure it out.

---

### Post by Eshu on 2007-04-21
Ok, here is the video and monitor sections. The modeline sets the screen properly when using xvidtune, but when I restart the X session it goes back to the default location.  Again, thanks for any help.

```

Section "Device" 
        Identifier      "GeForce_6200"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Viewsonic_VX900"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-75
        Modeline "1280x1024"   108.00   1280 1348 1460 1688   1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen" 
        Device          "GeForce_6200"   
        Monitor         "Viewsonic_VX900"
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

```

---

### Post by Eshu on 2007-04-22
Alrighty then. Completely rebooted the PC and now it works correctly with that modeline after enabling the desktop sfx.

---

