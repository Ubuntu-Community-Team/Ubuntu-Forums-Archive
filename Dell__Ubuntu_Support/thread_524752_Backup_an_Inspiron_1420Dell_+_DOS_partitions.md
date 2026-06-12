---
title: "Backup an Inspiron 1420/Dell + DOS partitions"
date: 2007-08-13
forum: Dell  Ubuntu Support
---

### Post by greatbuckets on 2007-08-13
So I've just got my new Inspiron 1420 preloaded with Ubuntu, and I've got to say that so far I'm impressed.  So much just seems to work OOTB, whereas I'm used to having to cajole a few things into working - function keys etc etc.  Nice.  Anyway, enough of the flattery!

Anyway, so normally I wouldn't worry about taking a backup of a virgin system as I'd just wipe the partitions and reinstall.  However, there are a couple of partitions that are unknown to me:

[FONT="Fixedsys"]
# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10         271     2104515    b  W95 FAT32
/dev/sda3   *         272         296      200812+  83  Linux
/dev/sda4             297       19457   153910732+   f  W95 Ext'd (LBA)
/dev/sda5             297         617     2578401   82  Linux swap / Solaris
/dev/sda6             618       19457   151332268+  83  Linux
[/FONT]

What is on the sda1 and sda2 partitions?  sda2 seems to contain a copy of DOS, presumably freedos?

How and when would these partitions be used, and what would happend if they were not there?  i.e. What is  the impact of me just wiping the hard drive, then doing a fresh install?

My understanding is that the Ubuntu CD that I got with the unit is a bog standard 7.04 release, so presumably these partitions wouldn't be used unless I instigated it after a re-install?

---

### Post by syssyphus on 2007-08-13
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions)

---

### Post by ivanlo2 on 2007-08-14
Before wiping your harddrive take a look at this thread 
[http://ubuntuforums.org/showthread.php?t=509408](http://ubuntuforums.org/showthread.php?t=509408)

There are a few snags trying to install  Ubuntu fresh from the liveCD. The CD  does not include hardware drivers required install Ubuntu, like Intel drivers, display drivers, ethernet, wireless, etc.  That thread has a few solutions you should look at.  After wiping my drive a few weeks ago I still don't have Ubuntu installed on my system and I'm waiting for someone to post a clone CD so I can install it on my laptop.  Seems like the simplest/easiest solution to be but you should look at the others posted on there.  Good luck.

---

### Post by smithno on 2007-08-14
This thread has been going on for a while. I posted in the beginning that I can't understand why folks want to wipe a Dell with Ubuntu pre-installed that has all of the configuration already done! Even when you wipe the system and install Ubuntu from scratch and track down all the Dell drivers/configuration bits, you still end up with the same starting point that Dell gave you. Also, if you don't wipe the restore partitions, you can put it back to factory fresh from Grub. 

Wiping Ubuntu to get rid of Gnome and install KDE is also needless. You can just install KDE from Gnome and switch window managers from the login screen. That's what I did. I am comfortable that I still have pretty much a stock base system with lots of stuff added. 

I still don't understand why anyone would wipe Ubuntu to re-install Ubuntu...:confused:

---

### Post by notwen on 2007-08-14
> **syssyphus said:**
> [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Default_Partitions)

Thanks, I've been looking for a Dell webpage that said officially which each partition actually is. =]

---

### Post by syssyphus on 2007-08-15
> **smithno said:**
> This thread has been going on for a while. I posted in the beginning that I can't understand why folks want to wipe a Dell with Ubuntu pre-installed that has all of the configuration already done! Even when you wipe the system and install Ubuntu from scratch and track down all the Dell drivers/configuration bits, you still end up with the same starting point that Dell gave you. Also, if you don't wipe the restore partitions, you can put it back to factory fresh from Grub. 

Wiping Ubuntu to get rid of Gnome and install KDE is also needless. You can just install KDE from Gnome and switch window managers from the login screen. That's what I did. I am comfortable that I still have pretty much a stock base system with lots of stuff added. 

I still don't understand why anyone would wipe Ubuntu to re-install Ubuntu...:confused:

well I still don't understand why someone would not understand why someone who likes linux would not tinker with their new toy.

linux is not an os, it is a way of thinking... it is a "I desperately want to know how it ticks, and I desperately want to void my warranty"

besides, we no longer have microsoft's boot on our neck, I do not want to have dell's boot on my neck next, I sure as hell do not want to depend on their recovery partition... I would like to do fun things with this laptop, such as dual boot with other distros / etc.

telling a linux hacker to not tinker is like telling rms to work for microsoft.

good luck.

---

