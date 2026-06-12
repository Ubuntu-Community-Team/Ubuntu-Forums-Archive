---
title: "Access to USB disk"
date: 2006-06-03
forum: Desktop Environments
---

### Post by tellnes on 2006-06-03
Hei,

Since im going to upgrade to Dapper, i figured i wannted to do a backup over to a usb device for my files.

I bought a 200gb maxtor, Breezy automounts it, and i can access it, but i cant write to it, or delete.
The disk is formated NTFS, and i was wondering how i can access with write and delete permissions to this disk from my ubuntu distro.

Anything i need to download, or how do i change permissions on the disk..?

Regards 
Tellnes

---

### Post by exit3219 on 2006-06-03
Normally, Linux cannot write to NTFS partitions (that's Microsoft's fault, as they don't provide documentation). Writing to NTFS is still experimental, so I wouldn't suggest you to use it for backup purposes. Instead, format the drive with ext3 or fat32.

---

