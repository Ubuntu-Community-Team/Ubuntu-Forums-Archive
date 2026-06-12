---
title: "LCD refresh rate"
date: 2005-10-23
forum: Desktop Environments
---

### Post by mike2297 on 2005-10-23
I have a SyncMaster 193P.  I can't figure out for the life of me how to get it to display 1280x1024 @ 60 Hz by default.  I can manually set the refresh rate through gnome, but I want 60 Hz to be the default.  The Gnome login screen displays at 75, as do any games I play in winex at 1280x1024.  My monitor doesn't support this refresh rate.  When it is at 75, there is a black bar running down the right side of the screen and everything is squished.

I am using the fglrx driver.  Here are some relevant parts of my xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        BusID           "PCI:3:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
        Modeline "1280x1024" 108.00 1280 1328 1440 1688 1024 1025 1028 1066
        Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
        EndSubSection
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection

```

I got the above modelines from the output from the fglrx driver (in the xorg logs).  They're both for 60 Hz

How can I force the driver to use the above modelines??

---

### Post by mike2297 on 2005-10-25
*bump*

---

### Post by mike2297 on 2005-10-26
sigh....*bump*

---

### Post by jdtanner on 2005-10-26
Why not just edit your xorg.conf file with the correct parameters? Your VertRefresh is set so that it allows a rate of 75Hz. Change that line so that it says 60 (not 56-75). 

I think in a terminal

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup*

then

*sudo gedit /etc/X11/xorg.conf *

should allow you to edit the necessary file. You could also type *man xorg.conf* in a terminal or have a read of [http://www.x.org/X11R6.8.2/doc/xorg.conf.5.html](http://www.x.org/X11R6.8.2/doc/xorg.conf.5.html).

Cheers,
JohnT

BTW, somebody will reply to you sooner or later...no need to sigh ;-)

---

### Post by mike2297 on 2005-10-26
Tried it, for some reason it doesn't work :( 

The fglrx driver is overriding the X setting and just choosing what it thinks is best or something...

-Mike

---

### Post by HermanAB on 2005-10-26
Hmm, did you remember to restart X after editing xorg.conf to 60Hz?

---

### Post by mike2297 on 2005-10-31
Yes, I did restart X.  Both with Ctrl-Alt-Backspace and also with stopping gdm and killing all X processes. But when I would start up X again, it would use the old settings.

Oddly enough (I don't understand this at all), the new changes weren't loaded until I reset the computer...  so all is well now.  Thanks!

---

