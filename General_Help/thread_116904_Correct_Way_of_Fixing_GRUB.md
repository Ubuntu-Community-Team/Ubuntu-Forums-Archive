---
title: "Correct Way of Fixing GRUB?"
date: 2006-01-13
forum: General Help
---

### Post by Unit #134679 on 2006-01-13
I used Windows and Ubuntu on two different drives. My Windows drive is master and my Ubuntu drive is slave. Whenever I have a problem with Windows and need to reinstall, the GRUB is removed or damaged or whatever. When I use the Ubunut disc and run the recovery mode I attempt to reinstall the GRUB the way the tutorials tell me. I would always either ruin on Windows drive and need to reinstall or GRUB would not install period. I used to just reformat the Linux drive and reinstall but I am getting tired of doing that

---

### Post by Greg2 on 2006-01-13
Here is a link to the easiest set of instructions for fixing GRUB that I’ve found on the forums. If your Windows drive is the master drive /dev/hda it should work for you.
[http://ubuntuforums.org/showthread.php?t=114332](http://ubuntuforums.org/showthread.php?t=114332)

---

### Post by handy on 2006-01-14
If your motherboard supports it, you can boot into your windoze drive even though it is on the secondary master IDE channel. 

If for some reason you lose the GRUB MBR & can no longer boot Ubuntu's drive, which is now on the primary master IDE channel, then just go into the BIOS & change the boot order.

This is how I have my machine set up.

If you have to reinstall windoze, it won't effect GRUB.

---

