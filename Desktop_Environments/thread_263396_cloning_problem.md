---
title: "cloning problem"
date: 2006-09-23
forum: Desktop Environments
---

### Post by rockyredhead on 2006-09-23
I have two hds - master 40gig with windows me - slave  80gig with ubuntu 6.06  with updates. There is a windows project that I need to complete before I can more or less abandon windows.

  As insurance I want a clone of my windows drive (reinstalling could be a nightmare as some stuff may not be available).  I have used knoppix and dd to copy the windows drive to an 80gig one.  I would like to have the old 40gig one as a backup.  I set the clone to master and replaced the 40gig windows with it but I do not get the grub menu and am not sure why or what steps to take to get my system to boot with the clone in place.
The cloning should have copied the MBR and all.  Fortunately I have caddies so swapping back was no problem.

I have not had cause to edit grub as yet but am willing to do this if needed.

Any pointers or suggestions would be appreciated.

---

### Post by kidders on 2006-09-23
Hi there,

Assuming you took a disk dump of your entire physical device, trying to dump it back onto a disk that's half the size *should* produce errors, afaik. If all you dumped was a single disk partition, you'll need to manually install Grub on your destination device at some point.

**Edit:** Just for clarity, dd-ing an entire disk *will* clone your MBR, assuming that's what you've done.

---

### Post by rockyredhead on 2006-09-23
The dump was from smaller to larger only.  Just can not get the grub menu with the larger in place of the smaller.

---

### Post by kidders on 2006-09-24
> The dump was from smaller to larger only.Yeah I figured that from your last post, but I thought I'd mention it, just to be safe.

What was the command you used to create the disk dump in the first place? (It has a bearing on the kinds of problems you might have.)

---

### Post by tagra123 on 2006-09-24
I personally prefer partimage to disk dumps except for backing up the mbr.  Won't help in this situation, but it may come in handy in the future.

---

### Post by rockyredhead on 2006-09-24
From memory the command was

dd if=/dev/hda1 of=/dev/hdb1

---

### Post by kidders on 2006-09-24
> **kidders said:**
> If all you dumped was a single disk partition, you'll need to manually install Grub on your destination device at some point.

You'll need to install grub. Once it's on, further disk dumps to individual partitions won't overwrite it ... well, obviously.

---

### Post by rockyredhead on 2006-09-25
what command would be used to copy everything from the 40g to the 80g
dd if=/dev/hda of=/dev/hdb ?????
Would that copy grub as well?
Would I need to use qtparted to get use of the whole 80g afterwards?
Thanks

---

### Post by kidders on 2006-09-25
Hey again,

> dd if=/dev/hda of=/dev/hdb ????? Would that copy grub as well?Yep, that's it exactly :-)

> Would I need to use qtparted to get use of the whole 80g afterwards?Yeah... It would clone the original partition table. 

There's nothing necessarily *wrong* about what you actually did though ... Often, when you recover a b0rked OS, you'll wind up needing to reinstall the bootloader anyway, if you want (or need) to make a hardware change that alters certain system settings.

---

