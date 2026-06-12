---
title: "Need Graphics Back :("
date: 2009-05-17
forum: General Help
---

### Post by tommo12 on 2009-05-17
Hey

i was trying to roll back my ATI driver because i was getting some issues with the video playback. So I went to the Hardware driver section and went remove... Now I have no drivers to display video at all :(

How can I fix this problem, because the driver install from ATI is graphical? Ive been trying to mount a usb or ipod and cdrom and install it from there but i think its graphical...

Anyhelp even to get my a basic graphical display so I can do the rest 

thanks :)

---

### Post by cmost on 2009-05-17
at the command line, try entering the following:

sudo nano /etc/X11/xorg.conf

Scroll down in the file until you find the section that looks like this:
.
.
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx" #might say "ati"
.
.

Chage the Driver to "vesa"
Save the changes
type:  sudo reboot
See if that gets you back and running.  Note:  Once you're back in Gnome, go ahead and reinstall the ATI driver.  Good luck!  :p

---

### Post by tommo12 on 2009-05-17
I had to add the Line
 
Driver   "vesa" into the file
then i tried 
 
Driver "fglrx"
 
With no sucess.
They returned a small colourful Ubuntu logo x 4 across the top with distorted colours :(
 
Any ideas people :) Please I am dying to use it again :)

---

### Post by Yellow Pasque on 2009-05-17
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f
```
Reboot.

---

