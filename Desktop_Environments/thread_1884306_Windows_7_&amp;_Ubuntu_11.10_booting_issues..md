---
title: "Windows 7 &amp; Ubuntu 11.10 booting issues."
date: 2011-11-21
forum: Desktop Environments
---

### Post by ominence5 on 2011-11-21
[B]Good day to all!
[/B]
I recently bought a new external hard-drive to install Ubuntu.

I have Win 7 running already in my laptop (Acer Aspire 5920g) in its own separate hard-drive.

I installed Ubuntu 11.10 and I also installed grub in my new external hard-drive.  Now my problem is that if I dont have my Ubuntu hard-drive connected to the laptop @ startup, no booting options load. It just gives me "No such partition found - Grub rescue>" 

I found out that the Ubuntu installation edited/deleted my Windows 7 "bootmbr" and the only way to fix this problem was by booting my Win 7 repair disk and in command prompt typing "bootrec.exe\fixmbr & bootrec.exe\fixboot"

Having done this, my Win 7 started booting like normal @ startup, but when I want to boot my Ubuntu hard-drive it says "Missing Operating System" 

What can I do to fix this?

**Thanks in advance**

---

### Post by typhoon_tip on 2011-11-21
While I am not sure how to fix the current grub on the external hard drive (there is plenty of material on the net), I know how to make sure to install it properly in order to boot from there.

When you are installing, you should not choose "Install alongside your current OS", instead choose the last option ("something else" should be), then choose the device that you want to install to (usually SDA is your internal HD, SDB or SDC should be your external one, MAKE ABSOLUTELY SURE before starting to erase partitions !).

After you click next, you are presented with the partitions over that drive, so until this point is safe to operate and no damages can be made. You can install over existing partition EXT4, or you can erase all partitioning and create an EXT4 primary mounted on "/" (root) and a SWAP partition roughly a bit larger than your RAM size.

The last option is then "where do you want grub to be installed", choose carefully the SAME device (SDB or SDC) that you are partitioning.

The outcome of this should be:
- When you start the laptop without the external drive, windows just start straight up
- When you connect and boot from external drive, it may prompt you to start Ubuntu or Windows, either one should then work

---

### Post by Rubi1200 on 2011-11-21
Hi and welcome to the forums ominence5 :)

This has the solution to your issue:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by ominence5 on 2011-11-21
Thanks for the replies :)! I will try all of the above tonight!

I did speak to a friend of mine and he said I might have done a mistake with installing grub.  I selected my whole external hard-drive instead of "/dev/sdc1" which was my **/boot** partition of about 258mb in size.  I followed this tutorial [http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/")

Could this be the problem?  When creating a fresh install, should I install grub on the **/boot** partition?

---

### Post by typhoon_tip on 2011-11-21
> **ominence5 said:**
> Thanks for the replies :)! I will try all of the above tonight!

I did speak to a friend of mine and he said I might have done a mistake with installing grub.  I selected my whole external hard-drive instead of "/dev/sdc1" which was my **/boot** partition of about 258mb in size.  I followed this tutorial [http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/")

Could this be the problem?  When creating a fresh install, should I install grub on the **/boot** partition?

/boot is not a partition. Grub shall be always installed to the physical device (SDA, SDB...). The link provided above is the perfect solution anyway. :)

---

### Post by Black_Sector on 2011-11-21
You could try changing the boot order.

---

### Post by Mark Phelps on 2011-11-21
Ignore other suggestions ... and use the link that Rubi1200 provided.  That has the instructions you need.

---

### Post by ominence5 on 2011-11-23
Special thanks to Rubi 1200,

Great work! Got everything sorted. I'm liking Ubuntu a whole lot better!  

Keep up the great work!

---

