---
title: "help, broke xorg.conf..."
date: 2006-10-04
forum: Desktop Environments
---

### Post by kpm on 2006-10-04
Ok, I goofed... but I did make a back up... problem is I just don't know how to access it...
I have been attempting so many different permutations of xorg.conf to get my dual monitor set up working (still no success on that... just a mess on the laptop screen, barely usable, and a low refresh rate on the crt... but that is another story...).  I actually ran the xorg configuration again, but must have missed the keyboard section, because I am stuck in caps, so cannot get my way back into /etc/X11/xorg.conf to restore my backup xorg.conf file.

I booted up with an Ubuntu bootable CD, and thought I would be able to navigate to the xorg.conf file and mv the backup over the bad one... but I can't mount the 'Volume', the hard drive, where it resides.

Nautilus identifes my hard drive as '36.6 GB Volume' but I can't access it at all.  I know i need to mount it, but my attempts have thus far been fruitless.  Is this something the live CD can do, or am I out of luck because i cannot get my keyboard out of CAPS??  (and I have checked cap locks and any strange function keys... I am quite sure I screwed up xorg.conf and now xorg thinks my keyboard is some strange one that makes the caps lock and shift keys completely useless...

thanks for any help!

---

### Post by xXx 0wn3d xXx on 2006-10-04
Once booted press Ctrl + Alt + F2 and then your will be at a console. Then enter sudo nano /etc/X11/xorg.conf and make the nessesary changes.

---

### Post by kpm on 2006-10-04
> **xXx 0wn3d xXx said:**
> Once booted press Ctrl + Alt + F2 and then your will be at a console. Then enter sudo nano /etc/X11/xorg.conf and make the nessesary changes.

Thanks!  I have recovered xorg.conf!  I actually tried doing cntrl-alt-f2 before, but seemed to get no response at all...  I thought my caps keys, funtion keys, etc, were all but dead to me.  I was sort of locked in the console that appears when xorg.conf is broken... maybe I had to be a bit more patient as even this time the machine was taking its time to switch to the console.

now back to the dual monitor conundrum...

---

