---
title: "Xgl/compiz configuration advice wanted, please"
date: 2006-09-22
forum: Desktop Environments
---

### Post by n00b@linux on 2006-09-22
I have an IBM Thinkpad T40 with a 1.5GHz Pentium M and an ATi Mobility Radeon M7 LW [Radeon Mobility 9000].

I have tried following this thread:
[http://www.ubuntuforums.org/showthread.php?t=219336&highlight=Xgl+ATi](http://www.ubuntuforums.org/showthread.php?t=219336&highlight=Xgl+ATi)
and I did get an Xgl session working.   Well, I think I did.  

The problem was that the Gnome bootsplash came up but without any text.   Furthermore, once the Gnome desktop came up the panel bars were both there (top and bottom) but without any text.  Everything looked normal except there was no text - anywhere.   When I hovered my mouse over the spot where menus would be eg, Applications, Places, System, everything behave normally except no text would show up.   I could see that the menus were there because they changed colour when I selected on them (and they dropped down).  But, again, without any text.

Could someone please tell me where I've gone wrong?

My /etc/X11/xorg.conf file contains the following:
```

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
    Driver        "ati"
    BusID        "PCI:1:0:0"
    Option          "BusType" "PCI"
        Option          "AGPMode" "4"
        Option          "AGPSize" "32" # default: 8
        Option          "AGPFastWrite" "false" ## More stable this way.
        Option          "SWcursor" "false" ##"true" # More stable this way.
        Option          "EnablePageFlip" "true" # Faster.
        Option          "EnableDepthMoves" "true" ##"false" # More stable this way.
        Option          "RenderAccel" "true" ##false" # More stable this way
        Option          "AccelMethod" "XAA" # or XAA, EXA, XAA more stable
        Option          "DDCMode"
        Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "on" ##"false" # More stable this way.
        Option          "DynamicClocks" "on" ##"true"
        Option          "bioshotkeys"   "True"
        Option          "XAANoOffscreenPixmaps" "false" ##"true" # More stable this way.
    Option        "mtrr"    "on"
    Option        "VideoOverlay"    "on"
    Option        "OpenGLOverlay"    "off"
EndSection

Section "Extensions"
        Option         "Composite"    "Enable"
EndSection

Section "DRI"
    Mode    0666
EndSection

```I have set up the following bash script, /usr/bin/startxgl.sh:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session

```In /usr/share/xsessions/xgl.desktop I have:
```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

```I notice that I am using the 'ati' driver and not 'radeon' nor 'fglrx'.  As I understand it, 'radeon' and 'fglrx' do not work for my GPU (Radeon Mobility 9000) so I think I'm using the correct driver.

I've tried changing the ':1' in /usr/bin/startxgl.sh to ':0'  as I read somewhere that the 'ati' driver should specify ':0' but that didn't work at all.   In fact, the opposite occured.  Instead of getting a long delay while the Xgl server starts up, I got a really quick startup that you usually get with the normal X server.  When I loaded a terminal and typed 'ps -e | grep xgl' I drew a blank, ie. Xgl was not running.

I'm fresh out of ideas.  I was hoping someone could suggest why I'm getting no text in Xgl/Compiz.

kind regards

---

