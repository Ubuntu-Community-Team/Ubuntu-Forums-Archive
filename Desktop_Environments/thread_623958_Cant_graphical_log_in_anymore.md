---
title: "Cant graphical log in anymore"
date: 2007-11-26
forum: Desktop Environments
---

### Post by Fredrich2k on 2007-11-26
Hi

I added a 10.4 inch touch screen to my Notebook, Added a .rpm package (which i converted to .deb with alien) and took a reboot. I know only see something on that touch screen and not on the notebook. And when I disconnect the touch screen I get only text based log in on the notebook... Im thinking it has something to do with the Xorg...

> Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 640     480
                Modes           "640x480@60"
        EndSubSection
EndSection

From xorg.conf.. Something tells me that is wrong..

Can anyone help me? Im a complete nuub :(

---

### Post by Snowcat on 2007-11-26
This might be stupid and maybe you've already tried it, but did you try simply reconfiguring x?

```
 sudo dpkg-reconfigure xserver-xorg -phigh
```

If I'm not mistaken, it should ask a few questions and recreate the relevant portion of your xorg configuration.

---

