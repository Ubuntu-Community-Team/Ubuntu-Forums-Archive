---
title: "Drive, permissions"
date: 2009-01-27
forum: General Help
---

### Post by tullmejs on 2009-01-27
I formatted a non-system external hard disk drive to ext3. Another one I left with Ntfs. Then I reinstalled the OS (on a third drive). Now the one with Ntfs is at 777 while the one I formatted is 755. I can't use it. How do I manage permissions in this case?

(I use xubuntu, in case that matters).

---

### Post by carolinason on 2009-01-27
list the drive by ```
sudo fdisk -l
``` mount the drive (assuming the drive is sdb1) ```
mount -t ntfs-3g /dev/sdb1 /mnt/mount_point/
```

---

### Post by tullmejs on 2009-01-28
It's the ext3 drive that I am not allowed to access. It mounts, I think, automatically. 

Here is the intriguing results of sudo fdisk -l:

```
tullmejs@s:~$ sudo fdisk -l
[sudo]
password for tullmejs:

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device	Boot	Start	End	Blocks	   Id	System
/dev/sda1	[COLOR="Red"]*[/COLOR]       1	4818	38700553+  [COLOR="Red"]83[/COLOR]	Linux

/dev/sda2		4819	5005	1502077+    5	Extended

/dev/sda5		4819	5005	1502046	   82	Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6b2fd1b

Device	Boot Start   End	Blocks		Id	System
/dev/sdb1    1	     60801	488384001	[COLOR="Red"]83[/COLOR]	Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6b2fd63

Device	   Boot	Start	End	Blocks	  Id	System
/dev/sdc1  [COLOR="Red"]*[/COLOR]	1       60801   488384001 7	HPFS/NTFS
```

I don't know why sdc1 is marked boot. Is it a problem?

I don't suppose that it is a good thing that sdb1 shares Id with sta1! But I don't know what to do about it. Do I need to repartition sbd1? It's empty so I guess I could try that. Thank you.

---

### Post by tullmejs on 2009-01-28
Tried that; drive still at Id 83, permissions 755. Now what?

---

### Post by tullmejs on 2009-01-28
I could format it to NTFS again, but there must be a better way.

---

### Post by tullmejs on 2009-01-28
Thank you, but again, the NTFS drive works (kind of). It is the Ext3 drive that shuts me out!

---

### Post by tullmejs on 2009-01-28
> **tullmejs said:**
> 
I don't suppose that it is a good thing that sdb1 shares Id with sta1!

Oh, just pulling your legs. :oops: 'Id' is obviously not unique identifier but file system shorthand, so naturally both "Linux" partitions are 83. I knew that.

---

### Post by tullmejs on 2009-01-28
Resolved, of sorts.

I made a directory that I chmoded 777, using it as I would have used the main dir of the drive.

---

