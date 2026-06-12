---
title: "Booting without a monitor"
date: 2005-12-09
forum: General Help
---

### Post by gk1980 on 2005-12-09
I've just installed Ubuntu 5.1 on one of my old PCs. (PII 300, 256M RAM, 9GB HD).

I want this machine to be a headless machine, meaning without a monitor, keyboard and mouse and simply stick somewhere in the house (using a wireless connection, ofcourse).

The problem is that I can't get it to boot without the monitor attached. I've changed the the entry in the BIOS to not stop on any errors.

I think the problem is with GRUB, but I'm not sure.

Will appreciate the help.

---

### Post by DrBair on 2005-12-09
You sure its the monitor? I've heard of BIOSs complaining about no keyboard but no monitor is something new.  AFAIK grub doesn't know much about attached monitors.  
Does it start to load up at all? Have you tried connecting the monitor after the fact and seeing what comes up on the screen?

---

### Post by Ferrat on 2005-12-09
Could be a problem with the GRUB or the OS, hard to tell since you can't say where it stops ^^

The bios shouldn't pose a problem with the monitor, the keyboard could be a problem but the "Don't stop on any errors" should fix that. 

What you could try is faking a monitor, for this you need a contact (can usally be bought at a electronics shop) and a schamatic for how to connect the pins. 

If it really is the monitor that does it, test started with just a monitor and see if it boots ok?

---

