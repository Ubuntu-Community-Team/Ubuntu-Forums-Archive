---
title: "BIOS/RAM problem?"
date: 2009-01-01
forum: General Help
---

### Post by redonwhite on 2009-01-01
My set up.
Motherboard : Asus M2N-SLI Deluxe AM2
CPU:  AMD 64bit X2 5200 Windsor
Ram: Corsair XMS2 2GB (2 x 1GB) , and Corsair XMS2 4GB (2 x 2GB)
Hard drive 1:  Western Digital with XP
Hard drive 2:  Western Digital with Ubuntu

My problem.
This started to occur after I recently installed an extra 4GB of RAM.  When I boot up my computer nothing pops up.  No BIOS screen or anything.  Then after I hit the reboot button the BIOs screen pops up.  Then it says that that my last boot session failed and I can either hit F1 to continue or delete to enter set up.  So I first hit F1 for continue and it successfully takes me to the black screen where i get the option to either boot up XP or Ubuntu.  I  choose Ubuntu and the Ubuntu loading screen pops up.  This screen then Freezes.  I reboot again and this time choose to enter my BIOS set up.  I look around but don't find anything worth fiddling with that would help my problem.  So I then Exit my BIOS and try loading Ubuntu again.  This time it works and I am able to log in.  My thoughts are that it has something to do with the extra 4GB of RAM i have installed recently as this hasn't happened before.  This situation does not happen all the time.  After I installed my RAM and booted up my computer everything seemed fine.  This situation happens every other time or so i boot up my PC.  Is there something in my BIOS i need to tweak because i installed new RAM?

---

### Post by 5BallJuggler on 2009-01-01
i may be wrong, but i thought motherboards and Bios only accept up to 4Gb of RAM, try removing your 2 x 1Gb and try again.

---

### Post by linux_tech on 2009-01-01
Try reseating all the RAM to make sure they are in the slots fully.
Then run memtest86, to see if there are any errors.

---

### Post by redonwhite on 2009-01-01
> **5BallJuggler said:**
> i may be wrong, but i thought motherboards and Bios only accept up to 4Gb of RAM, try removing your 2 x 1Gb and try again.

My motherboard can support up to 8GB of RAM.

---

### Post by redonwhite on 2009-01-01
> **linux_tech said:**
> Try reseating all the RAM to make sure they are in the slots fully.
Then run memtest86, to see if there are any errors.


I will make sure that they are in their slots fully.  Ill have to wait for another day to do a memtest86 though.

---

### Post by redonwhite on 2009-01-02
UPDATE:  I Flashed my BIOS.  Made sure all RAM was installed securely.  Nothing worked.  If anything it made it worse because when booting up my computer I wouldn't get anything on screen.  Not even my BIOS flash screen.  So i then decided to take out the 4GB i installed.  Waa laa.  All better now.  But I would really like to use those 4GB of RAM.  I dont see why i cant.  My mobo supports up to 8GB.  Both XP and Ubuntu recognized the total 6GB i had installed when i could boot into an OS.  Any ideas?  Id hate to have to RMA these sticks.

---

