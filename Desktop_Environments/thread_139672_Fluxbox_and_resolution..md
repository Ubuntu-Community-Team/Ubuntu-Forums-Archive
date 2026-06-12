---
title: "Fluxbox and resolution."
date: 2006-03-04
forum: Desktop Environments
---

### Post by ruvil on 2006-03-04
Hello!
I installed fluxbox today and it went fine, everything works perfect but there is one thing: i cant find where i can change resolution. Anyone knows how to change the resolution in fluxbox?

---

### Post by taurus on 2006-03-04
Look in /etc/X11/xorg.conf especially the section about Screen, toward the end of the file...

---

### Post by ruvil on 2006-03-04
oh yeah.. it looks like this:
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

if i want the 1024x768 res. should i remove everything else there and  just have 1024x768 there?

---

### Post by Xian on 2006-03-04
[QUOTE=ruvil]if i want the 1024x768 res. should i remove everything else there and  just have 1024x768 there?[/QUOTE]

The one that is listed first is the default.

---

### Post by taurus on 2006-03-04
Yes, remove everything before "1024x768"...

```

sudo gedit /etc/X11/xorg.conf
(Then it's the same password that you use to log in...)

```

---

### Post by Kagey on 2006-03-04
also try the command xrandr to change resolution on the fly.

---

### Post by ruvil on 2006-03-04
Thanks for the help everyone!
I have one last question: How do i change the refresh rate (hz) in fluxbox and others? 
I didnt find anything in the xorg.conf

---

### Post by taurus on 2006-03-04
[QUOTE=ruvil]Thanks for the help everyone!
I have one last question: How do i change the refresh rate (hz) in fluxbox and others? 
I didnt find anything in the xorg.conf[/QUOTE]
There is a section that gives you both vertical and horizontal refresh rates, just above section for Screen!!!

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

```

---

