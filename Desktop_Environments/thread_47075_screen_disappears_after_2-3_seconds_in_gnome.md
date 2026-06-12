---
title: "screen disappears after 2-3 seconds in gnome"
date: 2005-07-07
forum: Desktop Environments
---

### Post by mad_alfred on 2005-07-07
hi!
i've recently installed ubuntu on a toshiba satellite 1620cds laptop. Istallation wa fine, no error messages, but after 2-3 seconds the logon screen appeared the screen would turn black. I tried typing usr and psw and i noticed i could log into the system cause i heared the sounds ubuntu plays when u log in.

it's really strange..any suggetions?

---

### Post by varunus on 2005-07-07
Sounds like a video driver issue.  First, hit CTRL-ALT-F1.  Do you see a console login prompt?  If you do, log in and type
```
sudo /etc/init.d/gdm stop
``` 

After that, type
```
sudo nano /etc/X11/xorg.conf
``` 
This will edit your configuration file for X.

Scroll down to the Monitor section.  Is the screen resolution listed there too high for your screen?  If it is, turn it down and try rebooting.  If that doesn't work or isn't the problem, try changing your "DefaultDepth" option in the Monitor section to 16 from 24.  If that doesn't work, try changing the Driver in the "Device" section to "vesa" from whatever it is (will be something like nv, radeon, i810, etc).

Do any of these let you stay at the graphical login?

---

### Post by mad_alfred on 2005-08-01
[QUOTE=varunus]Sounds like a video driver issue.  First, hit CTRL-ALT-F1.  Do you see a console login prompt?  If you do, log in and type
```
sudo /etc/init.d/gdm stop
``` 

After that, type
```
sudo nano /etc/X11/xorg.conf
``` 
This will edit your configuration file for X.

Scroll down to the Monitor section.  Is the screen resolution listed there too high for your screen?  If it is, turn it down and try rebooting.  If that doesn't work or isn't the problem, try changing your "DefaultDepth" option in the Monitor section to 16 from 24.  If that doesn't work, try changing the Driver in the "Device" section to "vesa" from whatever it is (will be something like nv, radeon, i810, etc).

Do any of these let you stay at the graphical login?[/QUOTE]
 thank you so much!
now I can finally run ubuntu on my brother's pc :D ...and proove him that ubuntu is better than os x...

---

