---
title: "Modelines for Panasonic PX80?"
date: 2009-04-08
forum: Desktop Environments
---

### Post by soderman on 2009-04-08
I've now installed latest Nvidia drivers with envy. I got screen at my monitor connected with VGA, but I have big problem getting screen on my Panasonic PX80.

The TV only works with 1280x720 50Hz or 60Hz and 1920x1080 24Hz, 50Hz and 60Hz.

I read that I might have to add "modeline" in xorg.conf, and Ive generated with both "gtf" and Monitor Asset Manager 2.3 in Windows, but I cant get the TV to work.

Can someone please help me?

/Söder

---

### Post by bigbencg on 2009-04-08
The easiest way I know to correct your issue is to edit Xsetup and add a xrandr command.  First we need to make sure your resolution and refresh rate are in the current list of modes.  While logged in, open a terminal and enter the command ```
xrandr -q
```  This will list all available modes, make sure the mode you want is in the list.  Also take note of the name of the output, it should be listed in the second or third line and will say connected next to it.  This needs to be the output the TV will be connected to.  If 1280x720 is in the list, there should be one of more refresh rates listed to the right.  In terminal, enter ```
sudo nano /etc/gdm/Xsetup
```.  You don't have to use nano, I run kubuntu and like to edit with kate.  If you are unsure of a editor, nano will work.  I believe the Xsetup file resides in the directory I listed above, again I am running KDE and the file location is different.  Once in Nano use the arrow key to move the highlight box to the end of the file and enter your xrandr command.

Example:
```
xrandr --output TMDS-1 --mode 1280x720 --rate 60
```

CTRL+X out and save the file, then restart.  When X is loaded, the command will be executed and the display changed.  This will happen at the login screen.  If you wish to use another mode, simply replace the values above with your desired settings.  Again, make sure the output name is the output the TV is connected to.

---

### Post by soderman on 2009-04-09
This is my xorg.conf now, and it starts X, but my TV will not show it. I can start the computer, and log in with SHH and VNC, and then the resolution is 720p.

[http://biphome.spray.se/soder15/xstartar.txt](http://biphome.spray.se/soder15/xstartar.txt)

This is the log from X.
[http://biphome.spray.se/soder15/Xorg.0.log.txt](http://biphome.spray.se/soder15/Xorg.0.log.txt)

/Söder

---

### Post by soderman on 2009-04-09
This settings gives me screen on my TV
[http://home.bip.net/soder15/works.txt](http://home.bip.net/soder15/works.txt)

But its low res and overscan and it got red dazzles all over the screen.

If a change this:

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Option "UseEDID" "False"
EndSection

to this (disable Option "UseEDID" "False"):

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
# Option "UseEDID" "False"
EndSection

I no longer got screen at bootup
This is my new log.

[http://home.bip.net/soder15/log2.txt](http://home.bip.net/soder15/log2.txt)

/Söder

---

### Post by soderman on 2009-04-10
Case closed. My modelines from edid worked. Was a broken cable that gave me the red dazzle.

Thanks.

/Söder

---

### Post by ZyntaX on 2009-04-29
Hi !

I have the same tv as you and i have real big problems with configuring xorg.conf to get xbmc running.
Could you please re-up your working xorg.conf?
Also do you have working 1080p60 1080p50 1080p24 ?

Thanks

> **soderman said:**
> This settings gives me screen on my TV
[http://home.bip.net/soder15/works.txt](http://home.bip.net/soder15/works.txt)

But its low res and overscan and it got red dazzles all over the screen.

If a change this:

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
Option "UseEDID" "False"
EndSection

to this (disable Option "UseEDID" "False"):

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
# Option "UseEDID" "False"
EndSection

I no longer got screen at bootup
This is my new log.

[http://home.bip.net/soder15/log2.txt](http://home.bip.net/soder15/log2.txt)

/Söder

---

