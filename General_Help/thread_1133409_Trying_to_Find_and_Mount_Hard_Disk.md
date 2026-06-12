---
title: "Trying to Find and Mount Hard Disk"
date: 2009-04-22
forum: General Help
---

### Post by PirateChef on 2009-04-22
My friend just bought a new computer because his old one died. Unfortunately, the new one has a SATA motherboard, so his IDE hard disk doesn't work on it. 

I offered to borrow it and get the files off for him. It had a Windows system on it, so I figure it's formatted in NTFS. I plugged it in and booted up, and Ubuntu doesn't see it.

I got a good idea how to use mount, but how do I find out whether or not the device is even being recognized?

---

### Post by _Purple_ on 2009-04-22
Check with this command```
sudo fdisk -l
```

---

### Post by mshipman on 2009-04-23
Here's a sample scenario...

```

mshipman@VULPES:~$ sudo fdisk -l
[sudo] password for mshipman: 

Disk /dev/sda: 400.0 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50453   381424648+   7  HPFS/NTFS
/dev/sda2           50454       51681     9283680    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e874

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29999   240966936   83  Linux
/dev/sdb2           30000       30401     3229065    5  Extended
/dev/sdb5           30000       30401     3229033+  82  Linux swap / Solaris
mshipman@VULPES:~$ sudo mount /dev/sda1 /mnt
mshipman@VULPES:~$ sudo umount /mnt
mshipman@VULPES:~$

```

...If you get a dirty-flag message from the mount command, then you may want to mount the drive in windows first...

---

### Post by PirateChef on 2009-04-23
Hhhmmm....it's not showing up with fdisk, either.

> **mshipman said:**
> 
...If you get a dirty-flag message from the mount command, then you may want to mount the drive in windows first...

Unfortunately, that's not an option. I don't have Windows installed.

---

### Post by amingv on 2009-04-23
Checking if the BIOS is recognizing it should be the first step. Also you might want to double-check jumpers, just in case.

---

### Post by PirateChef on 2009-04-23
Good call!
The jumpers are missing. So, I guess there were two masters on that cable.

---

