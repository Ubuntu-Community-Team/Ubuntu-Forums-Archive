---
title: "USB disk Read-Only?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Robert Leithe on 2006-08-15
I have a Maxtor disk (USB), but I can't seem to be able to write enable it. Whenever I connect it, it pops up as read-only.

What do I have to do to be able to write to my disk?

Sincerely
Robert Leithe

---

### Post by orb9220 on 2006-08-15
Is it formatted in ntfs windows format?

Linux cannot write to ntfs partitions only read. Unless you use some addtional programs which on the whole is not recommended.

If you want the drive to be read and writeable for xp and linuc then it should be formatted to fat32.

---

### Post by Robert Leithe on 2006-08-15
Yes, it it formatted under WinXP.

So, this is the procedure then?

1) Copy everything from the USB disk to another 'disk
2) Format the USB disk from my Ubuntu client
3) Copy everything back to the disk
4) Voilà

Robert

---

### Post by orb9220 on 2006-08-15
If you want xp and linux to access it then fat32 wlse for just linux ext3.

Hope this helped.

---

### Post by Robert Leithe on 2006-08-15
I want both Linux and Windows to access the disk (at least in the foreseeable future), so I'll go with FAT32.

Thank you for your help!

Sincerely
Robert Leithe

---

### Post by Robert Leithe on 2006-08-16
I can't seem to be able to format the disk...

---

### Post by michux on 2006-08-16
> **Robert Leithe said:**
> I can't seem to be able to format the disk...

You need to umount it first in order to format it.

```
umount /media/usbdisk
```

And then format it with a command like:

```
mkfs.vfat /dev/sdb
```

---

### Post by Robert Leithe on 2006-08-16
Thanks,

but if I would want to format it to ext3 anyway, what would the format command be then?

EDIT: I found (via the help system) that the command

mkfs.ext3 /dev/sdb

Did the trick.

Thank you for your help!

Sincerely
Robert Leithe

---

### Post by Robert Leithe on 2006-08-16
Well, maybe I was a little quick there. The disk IS formatted, but I still can't write to it.

See the two attached screen shots for details.

EDIT: I ran this command (as su)

chmod -v 777 /media/usbdisk

And now I can write to the disk.

---

### Post by DoctorMO on 2006-08-16
it's hard to know how you mounted it if it dosn't have any partitions.

---

### Post by Robert Leithe on 2006-08-16
After I formatted it, I simply switched the power to the disk off, then on again. And the icon popped up on the desktop as it usually do. No manual mount necessary.

---

### Post by linuxify on 2008-04-12
Hi,

Just came across this thread while looking for a solution to my USB HDD that turned read-only earlier today. Its a 120G drive partitioned to 100G - vfat and 20G - ext3. I need to keep the vfat for compatibility with windows only computers. Also, I have over 40G of data on it so reformatting is not an option. (Yes I do have backups...) 

Anyway, both partitions were being mounted read-only. Re-mounting was not making any difference.

The problem was solved by running fsck.vfat and fsck.ext3 on the drive.

Hope this helps someone.
:)

---

### Post by warp99 on 2008-04-12
> **linuxify said:**
> 

The problem was solved by running fsck.vfat and fsck.ext3 on the drive.

If there is an error on the drive according to your settings in the fstab file or the udev file it will default to mount as read-only (ro), so yes running fsck clears that up. 

You can also try to manually mount the drive with the -w parameter. Type 'man mount' (Yeah, I know it's funny) at the command line for more options.

---

