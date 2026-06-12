---
title: "Ubuntu 8.10 intrepid ibex xorg.conf intel low resolution possible fix"
date: 2009-04-14
forum: General Help
---

### Post by hiddenh on 2009-04-14
After scouring the forum here trying different methods to get my 22" 220SW9FB Widescreen 1680 x 1050 monitor resolution to stick and work on 8.10 Ubuntu Intrepid Ibex i finally found one that worked and i wanted to share my solution.

Chipset i865, Integrated Graphics Intel X3000

In the end it was Driver, HorizSync and VertRefresh options in xorg.conf that enabled all available resolutions for my monitor. I had to add them all.

Original post that i used for reference
[http://ubuntuforums.org/showthread.php?t=972062&highlight=8.10+ibex+screen+resolution&page=1]("http://ubuntuforums.org/showthread.php?t=972062&highlight=8.10+ibex+screen+resolution&page=2")

Remember to create a backup of xorg.conf before making changes!

Command to edit xorg.conf
```
gksu gedit /etc/X11/xorg.conf
```

Copy of my current xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 30-83
        VertRefresh 56-75
        Option "dpms"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Hopefully this will work for others.

---

