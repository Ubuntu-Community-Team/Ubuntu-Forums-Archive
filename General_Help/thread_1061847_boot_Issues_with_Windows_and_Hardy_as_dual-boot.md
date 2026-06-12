---
title: "boot Issues with Windows and Hardy as dual-boot"
date: 2009-02-06
forum: General Help
---

### Post by theDaveTheRave on 2009-02-06
Hello all,

I run an Ubuntu dedicated Laptop (personal), and have a dual boot desktop for work. I seem to be having a number of issues with the desktop and windows so I figured I would "re-install" windows.

However, I have a funny issue in that I can't boot up from the CD/DVD rom drive on the desktop??

I can confirm that the CD drive is enables in the boot menu, and that it functions (I use it all the time for running some help modules that are presented as a "film").

I'm not sure that I will be able to even re-install the windows partition without breaking the ubuntu partition... but if I could at least re-install windows I would be able to get Ubuntu back onto the machine quite easily (ie wubi or similar).

your help is greatly appreciated.

David.

ps, I am going to try booting into the Windows partition and seeing if I can run the disk from there?

---

### Post by overdrank on 2009-02-06
Hi theDaveTheRave I have moved your post to its own thread in hopes that you receive better support. :)

---

### Post by caljohnsmith on 2009-02-06
So what drives will your BIOS boot? Only the HDD? Or can you boot maybe a floppy or USB drive? Also, do you currently have Grub installed to your HDD?

---

### Post by theDaveTheRave on 2009-02-06
Overdrank

Thanks for the move, but I felt that the thread responses by caljohnsmith were going to be pertinent to my problems, and eventual solution.

caljohnsmith

I've managed to get everything to work now, and I've re-installed XP, which was in fact rather less painfull than I had expected it to be!

I have instaled the network drivers, but can only access the local intranet from the system, which is a bit strange, but not a big problem really.

However, and more worringly, I have lost my Ubuntu partition
 :-({|=
I am going to follow your various instructions from other threads and log onto the system with a live CD and copy over the Grub boot loader into the correct place.

thanks in advance once again.

David

---

### Post by theDaveTheRave on 2009-02-07
caljohnsmith

Unfortunately the copy of the grub into the various places, and changing the setup of the boot for windows hasn't helped.

but I'm in luck, all my personal files are in a /home partition.

So I'm going to load on intrepid... just for fun of course!

David

---

