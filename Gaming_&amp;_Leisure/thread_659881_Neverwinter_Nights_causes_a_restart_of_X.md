---
title: "Neverwinter Nights causes a restart of X"
date: 2008-01-06
forum: Gaming &amp; Leisure
---

### Post by TNT220 on 2008-01-06
I'm relatively new to linux and am trying to get the linux version of neverwinter Nights to run on Ubuntu 7.10 on an IBMT41 laptop. I've followed the guide on Biowares site and also the howto guide i this forum.

I installed as user in my home directory and the permissions seems to be right
and I usually runs it from a terminal within the nwn directory by typing ./nwn

The bink player works as I can play the separate movies with sound and everything, but whenever I run ./nwn my entire x session restarts without any error messages and I have to log on again, only evidence I can find of what went wrong is in the system log where it says "gdm[5683]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0" .

There might be other places to look but I wouldn't know where.  I do have compiz and emerald running.

My xorg.conf looks like this 
```

Section "Device"
Identifier "Radeon 9000"
Driver "ati"
BusID "PCI:1:0:0"
Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Radeon 9000"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1400x1050"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

``` 

and I've edited the nwn startup script to look like this

```

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
#export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@

```

maybe it's a lost cause, but I thught I'd try posting and see if someone here had an idea..

Thanks

---

### Post by BreathEasy on 2008-01-06
OK, the first thing I'd do is disable Compiz before running the game. Not only will the frame rate be higher if you get NWN working, but it might completely fix this problem or, if not, it will at least help to avoid future issues.

Press ALT+F2, type in

metacity --replace

Try NWN now.

If that doesn't work, I'd try changing the Default Depth and Depth values in your xorg.conf to 32 instead of 16, unless the card is having trouble handling it. Your res of 1400x1050 seems kinda odd though - is that right?

---

### Post by TNT220 on 2008-01-06
Thaks for the suggestion, but the metacity --replace didn't change anything and changing the depth values in my xorg.conf to 32 meant that the X server failed to start entirely :-(

yes 1400x1050 is a strange resolution, but it is the correct one. Many of IBM's T4x series with 14" monitors run in that resolution.

---

