---
title: "need help please"
date: 2009-01-20
forum: General Help
---

### Post by kintesh on 2009-01-20
hi

i am new to ubuntu. i have installed some ubuntu in my second hard drive but wile i was installing i had power cut and whole system went off. when i started the computer and load ubuntu it stuck on loading screen. all i see is light gray screen. so i want to uninstall and reinstall ubuntu. 

can any one tell me how to uninstall ubutnu with boot select menu? 

i used my 2nd whole 40GB hard drive for ubuntu. and i cant see that hard drive anymore in "My Computer" in xp.

now i only got one hard drive for xp and one for ubuntu. means i cant access both hard drives using one OS. 

can you tell me how to remove ubutnu with boot select form 2nd hard drive and make that hard drive appear on xp again

step by step if possible. 

thanks

---

### Post by taurus on 2009-01-20
You don't have to delete Ubuntu before you reinstall it.  Just boot from the LiveCD and go through the installing process.  When you get to the partition screen, pick the _Manual_ option and mount the first partition of your second harddrive (probably /dev/sdb1) to / and format it.  For the other partitions (probably /dev/sdb5), swap, you don't have to worry about that since the installer knows what to do with it.

---

### Post by kintesh on 2009-01-20
BUT  i want to UNINSTALL completely with boot select screen.

also can i make that hard drive work for both xp and ubuntu. right now i can see that hard drive in my xp.

---

### Post by lykwydchykyn on 2009-01-20
If you install Ubuntu on the second drive, XP won't be able to see it because it doesn't have the ability to read Linux filesystems.

---

### Post by taurus on 2009-01-20
> **lykwydchykyn said:**
> If you install Ubuntu on the second drive, XP won't be able to see it because it doesn't have the ability to read Linux filesystems.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by kintesh on 2009-01-20
> **taurus said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)

so you are saying that i should use Ext2 or Ext3 file system on my next install of ubuntu

right?

---

### Post by lykwydchykyn on 2009-01-20
> **kintesh said:**
> so you are saying that i should use Ext2 file system on my next install of ubuntu

right?

fs-driver works with ext2 and ext3, though I would be cautious in recommending to you (which is why I didn't).  Don't use ext2, use ext3 -- ext3 is journaled, which basically means if the power goes it the filesystem won't get corrupted.  Ext2 can go belly-up if it's not shut down properly.

Clarify something here: do you want Ubuntu reinstalled or not?  If you want it installed, there's no need to uninstall anything, just re-do an install.  If you want it gone and just want to use this disk with XP, then you can probably just use disk management in XP to erase it and create a new ntfs partition.

---

### Post by kintesh on 2009-01-20
thnaks for your help everyone

got it working this time with ext3

this thing is grate when you drag each windows you see effect. this much better than vista (waste of money for crape os).

than u ubuntu u saved me a lot of cash lol

---

