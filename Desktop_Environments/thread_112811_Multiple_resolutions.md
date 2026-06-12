---
title: "Multiple resolutions"
date: 2006-01-05
forum: Desktop Environments
---

### Post by gray380 on 2006-01-05
Hi,

How can I make a multiple selection for screen resolution?

The file **/etc/X11/xorg.conf** contains next lines:
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

But from the System - Preferences - Screen Properties one value is accessible to me only: 1280x1024

I prefer the 1400x1050. Could you help me?

Best regards,
Serhiy.

---

### Post by mo_x on 2006-01-05
You can add some more resolutions to the Modes line. I for example have:
Modes		"1024x768" "800x600" "640x480"
I guess you have a TFT/LCD monitor. You probably want to use it at its native resolution (1400x1050?)

---

### Post by DSab on 2006-01-05
Personally, I use xrandr to test possible resolutions :

xrandr without args gives a list of available resolutions (supported by the graphic card and successfully initialized in X)

xrandr -s 3 for instance, will switch to the third resolution in the order of the list. 

If a resolution is not available in the xrandr list, you can look in /var/log/Xorg.0.log to find why. Maybe the graphic card does not support the resolution, or the driver does not know how to ask it from the card.

---

### Post by frodon on 2006-01-05
Adding the hsync and vertsync parameters corresponding to your screen specification will solve your issue i think, details here : 
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by gray380 on 2006-01-05
[QUOTE=mo_x]You can add some more resolutions to the Modes line. I for example have:
Modes		"1024x768" "800x600" "640x480"
I guess you have a TFT/LCD monitor. You probably want to use it at its native resolution (1400x1050?)[/QUOTE]

Yes, indeed.

---

### Post by gray380 on 2006-01-05
[QUOTE=DSab]Personally, I use xrandr to test possible resolutions :

xrandr without args gives a list of available resolutions (supported by the graphic card and successfully initialized in X)

xrandr -s 3 for instance, will switch to the third resolution in the order of the list. 

If a resolution is not available in the xrandr list, you can look in /var/log/Xorg.0.log to find why. Maybe the graphic card does not support the resolution, or the driver does not know how to ask it from the card.[/QUOTE]

The output of xrandr:
SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 301mm x 230mm )  *60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none

But in the windoze I use 1400x1050 on the same laptop.

---

### Post by gray380 on 2006-04-04
When nobody wishes to help you, it is necessary to do all by yourself ;). 
The problem has been solved by installation and configuration of a package 855resolution.

brg,
Serhiy.

---

