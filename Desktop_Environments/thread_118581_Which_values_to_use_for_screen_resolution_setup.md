---
title: "Which values to use for screen resolution setup"
date: 2006-01-17
forum: Desktop Environments
---

### Post by knahrvorn on 2006-01-17
Just installed Ubuntu Breezy Badger on my laptop (Dell Inspiron 1300) which has a 1280x800 (WXGA) native resolution. However, I'm only able to select 1024x768 from the Screen Resolution utility, so I wanted to follow this guide: [http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

To do that I need some technical information about my screen. In the owner's manual I found something that might be usable, but I'm not sure everything I need is there. From the following manual quote, can someone help me with which values I need to specify where? Thank you in advance.

--------------------------------------
**Video**
Video type: integrated on system board
Video controller: Intel Integrated Graphics Media Accelerator 900
Video memory: Up to 64 MB of shared memory (when less than 512 MB system memory is installed.) Up to 128 MB of shared memory (when more than 512 MB system memory is installed)
LCD interface: LVDS

**Display**
Type (active-matrix TFT): 14.1-inch or 15.4-inch WXGA
Dimensions:
[LIST]
[*]Height: 189.8 mm (7.5 inches)
[*]Width: 303.7 mm (11.9 inches)
[*]Diagonal: 358.1 mm (14.1 inches)
[/LIST]
Maximum resolutions:
[LIST]
[*]WXGA 1280 x 800 at 262,144 colors
[/LIST]
Refresh rate: 60 Hz
Operating angle: 0° (closed) to 180°
Viewing angles:
[LIST]
[*]Horizontal ±40° typical
[*]Vertical +10°/–30°
[/LIST]
Pixel pitch:
[LIST]
[*]14.1-inch: 0.237 mm
[/LIST]
Controls: brightness can be controlled through keyboard shortcuts

---

### Post by furtivefelon on 2006-01-17
try opening /etc/X11/xorg.conf, the following command should be suffice:
```
sudo gedit /etc/X11/xorg.conf
```

scroll down to the part with Screen resolutions and add 1280x800 to each line (you should already have three basic res in place, namely 1024x768, 800x600, 640x420).. 

However, that didn't work for me, i had to delete all other res before the system will recognize my new one.. Not sure why..

Are you sure your widescreen res is 1280x800 and not 1200x800?

---

### Post by knahrvorn on 2006-01-17
Thank you for your reply.

[QUOTE=furtivefelon]scroll down to the part with Screen resolutions and add 1280x800 to each line (you should already have three basic res in place, namely 1024x768, 800x600, 640x420)..[/QUOTE]

Actually, it's already there. Here's what's in the relevant parts of my xorg.conf now (this is the result of running dpkg-reconfigure xserver-xorg:

```

Section "Monitor"
        Identifier      "Dell Laptop LCD"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     30-60
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Intel Default Card"
        Monitor         "Dell Laptop LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

```
 
> Are you sure your widescreen res is 1280x800 and not 1200x800?

That's what the papers say, at least. I'll have a go for 1200x800 instead.

---

### Post by knahrvorn on 2006-01-17
[QUOTE=knahrvorn]I'll have a go for 1200x800 instead.[/QUOTE]
Didn't work either, unfortunately.

---

### Post by knahrvorn on 2006-01-18
[QUOTE=furtivefelon]However, that didn't work for me, i had to delete all other res before the system will recognize my new one.. Not sure why..[/QUOTE]
Ah, at first I missed this line. I tried removing the other resolutions from the "Display" SebSections in the xorg.conf file, so only 1280x800 is left, and now it works! Great! Thanks a lot!

---

