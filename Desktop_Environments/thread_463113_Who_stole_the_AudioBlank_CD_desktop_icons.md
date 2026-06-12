---
title: "Who stole the Audio/Blank CD desktop icons?"
date: 2007-06-03
forum: Desktop Environments
---

### Post by mrhelpman on 2007-06-03
When I used to put an Audio or blank CD into my CD/DVD drive, an icon used to appear on my (GNOME) desktop.  This doesn't happen any more. Anyone know why. I found the icon very useful.

I have tried this on Dapper, Edgy and on a Feisty machine I have at work and none of the machines show the icons any more.

The automount feature is still working as an icon does show when I put in a usb memory stick/

Any ideas anyone?

John T.

---

### Post by BOBSONATOR on 2007-06-03
alt-f2, then 

gconf-editor

then go down to apps, nautilus, desktop,  and show visible volumes.

---

### Post by mrhelpman on 2007-06-04
> **BOBSONATOR said:**
> alt-f2, then 

gconf-editor

then go down to apps, nautilus, desktop,  and show visible volumes.

The "volumes_visible" tick box is already ticked so that is not the problem.

JT

---

### Post by mrhelpman on 2007-06-10
> **mrhelpman said:**
> 
Any ideas anyone?



I have still not got this working, but if this gives anyone any clues, I get the audio CD icon appearing if I reboot the machine when an audio CD is in one of my CD drives - just logging on and off does not make the icon appear; I have to re-boot.
JT

---

