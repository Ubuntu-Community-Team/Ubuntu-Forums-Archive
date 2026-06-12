---
title: "Slow Shutdown/Restart Icon to Shutdown screen"
date: 2009-01-08
forum: General Help
---

### Post by rwigle on 2009-01-08
When I have finished my long day toiling away at the old keyboard, it takes more than 30 seconds from the time I click on the "Shutdown/Restart" icon until I get the screen with "Shutdown, Restart" (etc.)

I BELIEVE this behaviour started after I removed an ATI video card and went back to the on-board Intel video.

In all other respects the system seems to be working fine.

Hardy 8.04.1
Gnome Desktop

Thanks in advance (well and after too...)

---

### Post by Titan8990 on 2009-01-08
Did you remove your old ATI drivers?


As a work around you can shutdown and restart via the terminal:


Shutdown:


sudo shutdown -h now


reboot:

sudo shutdown -r now

or

sudo reboot

---

### Post by mssever on 2009-01-08
> **Titan8990 said:**
> Shutdown:


sudo shutdown -h nowor sudo poweroff

or sudo halt

> reboot:

sudo shutdown -r now

or

sudo reboot

---

### Post by rwigle on 2009-01-08
I THOUGHT I removed the ATI drivers, but I am not 100% sure.. How do I figure this out?

---

### Post by Titan8990 on 2009-01-14
the lsmod command will tell you whether or not in the ati module is in the kernel. 

Not exact but the name is something like:


flgrx

---

