---
title: "[SOLVED] full drive capcity not available after erase"
date: 2008-12-12
forum: General Help
---

### Post by os.getlogin on 2008-12-12
Hey all.  I have a 250GB seagate barracuda (7200.10) that I wiped clean with [Secure Erase]("http://cmrr.ucsd.edu/Hughes/SecureErase.html").  Now, after hooking up as an external drive I'm only able to format and "see" 137GB:

> 
% sudo fdisk -l
Disk /dev/sdg: 137.4 GB, 137438952960 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab586

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       16709   134215011   83  Linux


Any ideas?  Is the mbr corrupt?  Is there a way to wipe the mbr clean and start anew?

-Nate

---

### Post by ibuclaw on 2008-12-12
The mbr (master boot record) is only the first 512kb of the hard disk, and is only used if your drive is "bootable" (runs a boot manager to load an operating system)

This... is something of a different nature.

Never seen anything like this happen before.

Have you tried any other application to see how much space the hard drive has? ie: **gparted**
Maybe run an **fsck** scan on the hard drive ?

Also, can you post the output of this hdparm check ?
```
sudo hdparm -I /dev/sdg
```

Another piece of confirmation that you can check, is rebooting into BIOS and if the external hard drive is detected, find out how much capacity the motherboard thinks it has.

Regards
Iain

---

### Post by geirha on 2008-12-12
The MBR has nothing to do with the size of the disk. The size you see is approximately 128GiB, which means some hardware or software between your drive and the computer has a limit of 128GiB. What operating system are you using? and which version? Is it an IDE disk or SATA disk? How is it connected?

---

### Post by unutbu on 2008-12-12
Seagate discusses the problem:

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SATA_Troubleshooter_-_137_GB_Capacity_Issues&vgnextoid=d8344a3cdde5c010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SATA_Troubleshooter_-_137_GB_Capacity_Issues&vgnextoid=d8344a3cdde5c010VgnVCM100000dd04090aRCRD)

It appears the drive may have been "clipped to a lower capacity."
If this guess is true, you should be able to reset the capacity using [Seatools for DOS]("http://seatools.seagate.com/")

---

### Post by CatKiller on 2008-12-12
> **os.getlogin said:**
> Now, after hooking up as an external drive I'm only able to format and "see" 137GB

You're using 28-bit addressing. The 137 GB (128GiB) limit is well-known and was solved by 2001. Either your drive is jumpered to only use 28-bit addresses (an option for backwards compatibility on some drives) or your external drive enclosure is a bit rubbish.

Possibly 48-bit LBA (Logical Block Addressing) is disabled somewhere else, but I'd imagine that it's the drive controller in the enclosure that's to blame.

---

### Post by os.getlogin on 2008-12-13
> **tinivole said:**
> The mbr (master boot record) is only the first 512kb of the hard disk, and is only used if your drive is "bootable" (runs a boot manager to load an operating system)


Ok, thanks for the clarifying the mbr.  I was thinking that list of partitions was corrupt, but this obviously had nothing to do with it.

> **tinivole said:**
> 
**gparted**
Maybe run an **fsck** scan on the hard drive ?


Yes, gparted, fsck, fdisk, all showed the same thing.

The strange this is that in my external enclosure and on two different machines (linux and windows) a different 250GB drive showed up at full capacity.  So it seems it's the drive.  But the drive *used* to show up as 250GB.  So it seems Secure Erase did something to it.

> **geirha said:**
> The size you see is approximately 128GiB, which means some hardware or software between your drive and the computer has a limit of 128GiB. 

Ok.  This got me one step closer.  I had no idea that 137GB (128GB) was a magical number.

> **unutbu said:**
> Seagate discusses the problem:
It appears the drive may have been "clipped to a lower capacity."
If this guess is true, you should be able to reset the capacity using [Seatools for DOS]("http://seatools.seagate.com/")

Here we go.  This was the magic.

> **CatKiller said:**
> You're using 28-bit addressing. The 137 GB (128GiB) limit is well-known and was solved by 2001. Either your drive is jumpered to only use 28-bit addresses (an option for backwards compatibility on some drives) or your external drive enclosure is a bit rubbish.

Possibly 48-bit LBA (Logical Block Addressing) is disabled somewhere else, but I'd imagine that it's the drive controller in the enclosure that's to blame.

It turns out that the 1.x version of the Seatools on my [Ultimate Boot CD]("http://www.ultimatebootcd.com") did not work.  Using the new graphical version pointed out at [Seatools for DOS]("http://seatools.seagate.com/") (v. 2.07), the drive was listed at 137GB, but I was able to "set" the drive capacity in the advanced menu to "Max" which changed it to 250GB. 

So in the end the 28-bit addressing limitation seemed to be reset somehow by [Secure Erase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml") on the drive itself.

Thanks for all of the suggestions and help.

-Nate

---

