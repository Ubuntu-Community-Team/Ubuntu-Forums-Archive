---
title: "Problem installing Ubuntu 6.06LTS"
date: 2006-09-07
forum: Desktop Environments
---

### Post by gleswaran on 2006-09-07
Hi there, 
I just downloaded the iso image of ubuntu for desktop pc user. When i put in a new hdd and booted up the system with the live cd, all goes well whereby i can see the spash image and can select 'enter' to commence installation. However, here in lies the problem. I get stuck at the very first step after linux un-packaging is successful. The following are the error messages which i get.
[4294805.284000] hdd: ide_intr: huh? expected NULL handler on exit
[4294826.531000] hdd: ide_intr: huh? expected NULL handler on exit
[4294826.581000] buffer I/O error on device hdd logical block 357298

and the list goes on repeating the above messages. I tried installation with 3 hdds and still got the same problem. Can anyone please help as i'm looking forward to switching to ubuntu from xp.
cheers

---

### Post by lagagnon on 2006-09-07
I suspect something is wrong with your hard drives, the hard drive connections to the motherboard or your BIOS. When you computer first boots up go into your BIOS setup and make sure it is detecting your hard drives correctly.

---

### Post by CatKiller on 2006-09-08
> **gleswaran said:**
> I get stuck at the very first step after linux un-packaging is successful. The following are the error messages which i get.
[4294805.284000] hdd: ide_intr: huh? expected NULL handler on exit
[4294826.531000] hdd: ide_intr: huh? expected NULL handler on exit
[4294826.581000] buffer I/O error on device hdd logical block 357298

and the list goes on repeating the above messages. I tried installation with 3 hdds and still got the same problem.

I don't think that the "hdd" refers to "hard disk **drive**", but rather "hard disk **D**" (as opposed to "hard disk **A**"), or rather the Secondary Slave - probably the cd drive that you're trying to install from.

I'd try the usual cd-related things - clean the disk, clean the lens, check the cables, check the MD5 sums, and so on.

---

### Post by rjdohnert on 2006-09-08
Its either a bad burn or your disk is dirty.  The I/O Buffer ussually is an indicator of one or another.  The other possibility is your drive is dying, try reburning the ISO images.

> **gleswaran said:**
> Hi there, 
I just downloaded the iso image of ubuntu for desktop pc user. When i put in a new hdd and booted up the system with the live cd, all goes well whereby i can see the spash image and can select 'enter' to commence installation. However, here in lies the problem. I get stuck at the very first step after linux un-packaging is successful. The following are the error messages which i get.
[4294805.284000] hdd: ide_intr: huh? expected NULL handler on exit
[4294826.531000] hdd: ide_intr: huh? expected NULL handler on exit
[4294826.581000] buffer I/O error on device hdd logical block 357298

and the list goes on repeating the above messages. I tried installation with 3 hdds and still got the same problem. Can anyone please help as i'm looking forward to switching to ubuntu from xp.
cheers

---

