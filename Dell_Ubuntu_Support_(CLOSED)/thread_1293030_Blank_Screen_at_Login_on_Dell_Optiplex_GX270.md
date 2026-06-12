---
title: "Blank Screen at Login on Dell Optiplex GX270"
date: 2009-10-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aubreyisland on 2009-10-16
I just installed 9.04 on a Dell Optiplex GX270 at work and noticed something funny. Upon start-up I end up with this blank screen and I don't notice the splash screen during boot - it just sits there. I can tell the monitor is on (not off), so, I hit CTRL+ALT+BACKSPACE and walla!, the login screen shows up. Wierd...

Anyways, I am going to do a quite boot-up (no splash) and see what happens...

Any ideas?

---

### Post by lykwydchykyn on 2009-10-16
I've put Debian and Ubuntu on GX270, GX260, and GX60 machines and I've always found it's best to update to the latest BIOS.  They all (if memory servers) have an Intel 845 graphics chipset on the MB which has issues with the Linux Intel driver if the BIOS is not up-to-date.

You can actually do this via apt-get with a little setup, see this:

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

---

### Post by aubreyisland on 2009-10-16
Actually, I did a no spash non-quite boot and noticed that hang was happening on the swap file activation???

I did a CTRL+ALT+DELETE <- Correction and it, for some reason, stopped trying and continued...

This might actually have something to do with my setup. I had Windows XP on it before and installed using the "In Windows" option...

---

