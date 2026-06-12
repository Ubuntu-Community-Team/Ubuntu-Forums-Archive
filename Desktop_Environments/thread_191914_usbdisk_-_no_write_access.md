---
title: "usbdisk - no write access"
date: 2006-06-08
forum: Desktop Environments
---

### Post by oyvindaa on 2006-06-08
Hi.

I've got a usbdisk / mp3 player and it mounts just fine, but when I try to add any files it says I haven't got any write access.

I've tried different things, like adding it to fstab.

/dev/sda1       /media/usbdisk  auto    users,gid=users,umask=0000,defaults

After applying that line it says I've got all the rights, but I still can't add any files.

I've tried "chmodding" it, but that was also unsuccessful.

The same problem occurs when I try to add files in Windows.

Anyone know a solution to this?

Thanks.

---

### Post by guzerat on 2006-06-08
The filesystem on the usbdisk is probably corrupted (possibly caused by not unmounting before unplugging it). You should try to rewrite it.

Something like this:
Make sure the usbdisk is **not** mounted. Then run "sudo mkfs.vfat /dev/sda1". Then remount it.

---

### Post by oyvindaa on 2006-06-08
[QUOTE=guzerat]The filesystem on the usbdisk is probably corrupted (possibly caused by not unmounting before unplugging it). You should try to rewrite it.

Something like this:
Make sure the usbdisk is **not** mounted. Then run "sudo mkfs.vfat /dev/sda1". Then remount it.[/QUOTE]

When I unmount it and type the "sudo mkfs.vfat /dev/sda1" command I get this message:

mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Attempting to create a too large file system

---

### Post by musicinmybrain on 2006-06-08
Use "sudo mkfs.vfat -F 32 /dev/sda1" to make a FAT32 filesystem instead of a FAT16 one. Also, you may want to use "-n volume_name" to give the volume a name. This is what it will show up as when mounted.

---

### Post by oyvindaa on 2006-06-08
[QUOTE=musicinmybrain]Use "sudo mkfs.vfat -F 32 /dev/sda1" to make a FAT32 filesystem instead of a FAT16 one. Also, you may want to use "-n volume_name" to give the volume a name. This is what it will show up as when mounted.[/QUOTE]

This is what happens when I use "sudo mkfs.vfat -F 32 /dev/sda1" :

oyvind@aassveen:/dev$ sudo mkfs.vfat -F 32 /dev/sda1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Too few blocks for viable file system

:(

---

### Post by musicinmybrain on 2006-06-08
Now *that's* confusing. Anyone know what's going on here?

---

### Post by Michal77 on 2006-06-28
[QUOTE=musicinmybrain]Use "sudo mkfs.vfat -F 32 /dev/sda1" to make a FAT32 filesystem instead of a FAT16 one. Also, you may want to use "-n volume_name" to give the volume a name. This is what it will show up as when mounted.[/QUOTE]

Hi,
I had the same problem. Can't write or move data from usb disk. I did how you wrote and works prefect now.
Thanx!
M.

---

