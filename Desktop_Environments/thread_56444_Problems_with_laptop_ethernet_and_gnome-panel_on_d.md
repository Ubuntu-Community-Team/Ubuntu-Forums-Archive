---
title: "Problems with laptop ethernet and gnome-panel on different networks"
date: 2005-08-12
forum: Desktop Environments
---

### Post by dehuszar on 2005-08-12
So far I've really been enjoying Ubuntu, but there have been a few little kinks that have been quite aggravating.  The most aggregious of them is that when I leave my home network and go to a different one (I'm a consultant so this happens all the time), if I boot the machine with an ethernet cable plugged in, once I log in, I'll get a blank brown screen, with blank gnome-panel bars at the top and bottom of the screem, --essentially, no desktop.  

Right-clicking doesn't give me any menu to go to a command prompt with, and I essentially have to Ctrl-Alt-Bkspc to the shell and sudo halt, unplug the ethernet cable, and then boot again.  Now, if there's a WiFi network nearby that my Broadcom thinks it can talk to....  you guessed it.  

Only this time, I have to go into the BIOS and disable the damned thing until I get home.  Needless to say, this is not an ideal working environment.  Is there anyone else out there who has seen this sort of thing?  At first I thought it was something the desktop was trying to gather through my keyring file (I had Samba mounting passwords held in the keyring) and couldn't, and so I emptied all entries using the  keyring manager, and unmounted all Samba and SSH connections which might try and remount at boot, but it still didn't seem to help me.

Thanks in advance for any assistance you might be able to provide.

Samuel deHuszar Allen

---

### Post by dehuszar on 2005-08-16
Anyone?

---

