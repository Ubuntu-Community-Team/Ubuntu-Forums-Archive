---
title: "NTFS checking outside Windows"
date: 2008-12-11
forum: General Help
---

### Post by guitarMan666 on 2008-12-11
My friend and I are in the process of preparing her computer for an Ubuntu install.  We have run into a myriad of problems, which is something new to me when it comes to Ubuntu installs.  The only option she has is to use her whole disk and this is her preferred option because GParted and Ubiquity's partition editor refuses to allow a resize of her NTFS partition.

In the process of setting up her XP installation to share to a Vista computer for backup purposes, we hosed up HAL.dll in the required patching process.  This has rendered XP un-bootable and the drive un-mountable pending a consistency check with her files trapped inside.  I am certain that the partition will mount if we can fix the errors that surely reside on that partition.  I need a Linux alternative to 'checkdsk' so that we do not have to resort to PhotoRec to recover the files.  If anyone knows of one it would be EXTREMELY appreciated.  We are working from the Ubuntu LiveCD system right now (if that makes a difference).

Thanks in advance for the help!

---

### Post by geirha on 2008-12-11
As far as I know, there is no utility to fix NTFS filesystems on linux because Microsoft keeps the specifications for NTFS secret. Your best bet is to boot a Windows cd and run chkdsk from that.

As for the resizing; gparted will not be able to resize NTFS partitions if the filsystem is too fragmented, so if gparted fails when resizing an NTFS partition, you want to boot into windows and do a defragmentation on it.

---

### Post by nzadLithium on 2008-12-11
stick the hard disk in another windows pc, boot it up, get it to checkdisk it, then take it back to the original pc, and do what you want :D

---

### Post by guitarMan666 on 2008-12-11
Thanks so much I will try both of these options.  However, we did already defragment the hard drive before attempting the resize and it didn't change anything.  

This is infuriating enough to keep me on a non-MS system for quite some time to come though lol.

---

### Post by nzadLithium on 2008-12-11
Ubuntu won't let you resize in two cases I think, 
1) the drive isn't defragmented, some people have had to defragment 2 or 3 times before ubuntu decides its safe.
2) the drive is mounted you would need to open a terminal and type 
   sudo umount /dev/(drivedevice)

---

### Post by guitarMan666 on 2008-12-14
I see.  Is is possible to defrag from inside Linux?

---

### Post by snova on 2008-12-14
Probably not.

The specifics of NTFS are not known, but enough knowledge has been compiled through reverse engineering where we can put together a driver of sorts. But not a lot more than that.

---

### Post by guitarMan666 on 2008-12-14
Figures.  Well ok I'll figure something out when I'm done cursing and swearing over here. lol

---

