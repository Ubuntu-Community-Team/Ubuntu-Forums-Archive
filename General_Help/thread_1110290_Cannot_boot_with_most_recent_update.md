---
title: "Cannot boot with most recent update"
date: 2009-03-29
forum: General Help
---

### Post by Mooseknuckle on 2009-03-29
I'm running the latest version of Jaunty, and after this morning's update, I cannot boot anymore.   I get the following message:

Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/8b37250c-8612-45b2-bf05-6f8b0ced3c3c does not exist.  Dropping to shell!

I CAN boot to older generic kernels listed in my /boot/grub/menu.lst however, but the X server wont properly start (thats another issue).  The boot device is /dev/sdb1

Here is the output of blkid:
```

/dev/sdb1: UUID="8b37250c-8612-45b2-bf05-6f8b0ced3c3c" TYPE="ext3" 
/dev/sdc1: TYPE="ntfs" UUID="84481BFB481BEAA6" LABEL="System" 
/dev/sdb5: TYPE="swap" UUID="ac6f2472-073d-4816-9525-b62d305ba0e8" 
/dev/sda1: UUID="52b55cd5-1a64-40fc-adf2-05bc4fb283db" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="1dc03129-27d9-41bf-85c4-44a79e445c20" SEC_TYPE="ext2" TYPE="ext3" 
```


Here is the output of fdisk -l:
```


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9d4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x769a769a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b184b17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c821d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux


```

And here,  is the grub entry for the one that wont boot:

```

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8b37250c-8612-45b2-bf05-6f8b0ced3c3c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```

Anyone know what might be going on here??   Thanks much for any help!

---

