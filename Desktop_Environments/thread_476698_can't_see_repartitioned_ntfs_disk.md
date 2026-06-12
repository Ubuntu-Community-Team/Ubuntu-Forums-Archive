---
title: "can't see repartitioned ntfs disk"
date: 2007-06-17
forum: Desktop Environments
---

### Post by RamonV on 2007-06-17
I have ubuntu 7.04. I have a double boot system with XPsp2 on the other side.
I have a ntfs disk I recently could see from the gnome desktop file manager. I had 2 volumes on the disk, one ntfs other ext3. I then modified partitions with 7tools' Partition manager (7pm2005.exe on XP) and changed the disk, creating a single ntfs partition. Originally it was a dynamic disk and was somehow changed to a basic disk.

Now I can't see it from gnome ubuntu desktop. With the device manager I see it is set to volume.ignore=true, and I found a file (Inow can't find it anymore among such myriad of parameter files) that has that line, but I suspect it is a generated file, as it was in /org/... but I can't find that directory.

I searched in google and found a debian answer saying that the only solution was to reformat the disk, as somewhere there was inconsistent info in the partition table. I don't find that answer acceptable. Looks like windows! I have big movies in the disk and don't have the space elsewhere to move them and reformat.

Any help?

RamonV

---

### Post by dreadlord_chris on 2007-06-17
> **RamonV said:**
> I have ubuntu 7.04. I have a double boot system with XPsp2 on the other side.
I have a ntfs disk I recently could see from the gnome desktop file manager. I had 2 volumes on the disk, one ntfs other ext3. I then modified partitions with 7tools' Partition manager (7pm2005.exe on XP) and changed the disk, creating a single ntfs partition. Originally it was a dynamic disk and was somehow changed to a basic disk.

Now I can't see it from gnome ubuntu desktop. With the device manager I see it is set to volume.ignore=true, and I found a file (Inow can't find it anymore among such myriad of parameter files) that has that line, but I suspect it is a generated file, as it was in /org/... but I can't find that directory.

I searched in google and found a debian answer saying that the only solution was to reformat the disk, as somewhere there was inconsistent info in the partition table. I don't find that answer acceptable. Looks like windows! I have big movies in the disk and don't have the space elsewhere to move them and reformat.

Any help?

RamonV

what's the output of:
```

sudo fdisk -l

```

---

### Post by RamonV on 2007-06-17
root@rvm-hp:~# sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32
/dev/sda2   *         620       13609    98204400    7  HPFS/NTFS
/dev/sda3           13610       15117    11400480   83  Linux
/dev/sda4           15118       15505     2933280   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by mcduck on 2007-06-18
You need to edit your /etc/fstab to mount the new parition at boot. Check the correct UIID with 'ls -la /dev/disk/by-uuid' and make sure you use the correct UUID for your partition.

---

### Post by dreadlord_chris on 2007-06-18
> **RamonV said:**
> root@rvm-hp:~# sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         619     4679608+   b  W95 FAT32
/dev/sda2   *         620       13609    98204400    7  HPFS/NTFS
/dev/sda3           13610       15117    11400480   83  Linux
/dev/sda4           15118       15505     2933280   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

You need to make a mount point & add it to fstab...
Your device socket is **/dev/sdb1**, so let's get to it: first the mount point - you need to pick a NAME. From here on replace NAME with what you chose...
```

sudo mkdir /media/NAME
ls -l /dev/disk/by-uuid/

```
from the last commands output look for the line that ends with /sdb1 and copy the long string that comes before the ->
i.e.
```

lrwxrwxrwx 1 root root 10 2007-06-16 15:49 efe89fd9-58ab-456c-9881-528a9149e3c7 -> ../../sdb1

```
you would copy **efe89fd9-58ab-456c-9881-528a9149e3c7**, it's called the UUID. Now edit fstab as **root**
```

gksudo gedit /etc/fstab

```

At the bottom add the following 2 lines - replacing <<UUID>> with the UUID copied earlier, and NAME with the mount point you picked:
```

# /dev/sdb1
UUID=<<UUID>> /media/NAME ext3 nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2

```
save the file. Now back in the terminal:
```

sudo mount -a

```
if you get any errors post back....
Otherwise you're good to go...

---

### Post by RamonV on 2007-06-30
Thank you.

It was the mkdir /media/NAME that I was missing...

R.

---

