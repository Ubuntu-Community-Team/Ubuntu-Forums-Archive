---
title: "cant access my files on  windows drives"
date: 2009-02-27
forum: General Help
---

### Post by salman203 on 2009-02-27
i just got xubuntu installed after repartitioning on drive H of my system. my windows xp is installed on drive C while i have also an extended drive E
now the problem is when i go to "places"i cant see my media on drive c or E listed. how can i access those drives. previously i had ubuntu and i could easily access my windows folders too. any advice plz

---

### Post by iaculallad on 2009-02-27
Try to post whatever displays when you issue the terminal command below:

```
sudo fdisk -l
```

That's small letter 'L'.

---

### Post by salman203 on 2009-02-27
when i run the "sudo fdisk -l command in the terminal

i get the following "

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa967a967

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2777    22306221    7  HPFS/NTFS
/dev/sda2            2778        4864    16763827+   f  W95 Ext'd (LBA)
/dev/sda5            4080        4864     6297448+   7  HPFS/NTFS
/dev/sda6            2778        4018     9968269+  83  Linux
/dev/sda7            4019        4079      489951   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2055 MB, 2055208960 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9822

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         250     2007008+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(248, 254, 63) logical=(249, 220, 35)

---

### Post by iaculallad on 2009-02-27
You need to do some things in order for the NTFS partition to mount.

Create the mountpoint first:

```
sudo mkdir /media/Drive_C
sudo mkdir /media/Drive_E
```

Now the next thing to do is open /etc/fstab file for editing:

```
gksu mousepad /etc/fstab
```

and insert the lines of texts below on the last part of the file:

```
/dev/sda1 /media/Drive_C     ntfs    defaults,umask=007,gid=46 0
/dev/sda5 /media/Drive_E     ntfs    defaults,umask=007,gid=46 0  
```

Save and Close the file. While on the terminal, issue the command below:

```
sudo mount -a
```

HTH.

---

### Post by salman203 on 2009-02-27
i followed all the steps. in the end when i entered the final command in terminal i got this message:

[mntent]: warning: no final newline at the end of /etc/fstab
ntfs-3g: Failed to access volume 'dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

---

### Post by iaculallad on 2009-02-27
> **salman203 said:**
> i followed all the steps. in the end when i entered the final command in terminal i got this message:

[mntent]: warning: no final newline at the end of /etc/fstab
ntfs-3g: Failed to access volume 'dev/sda1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

Are you sure you copied the exact text I posted? Try to copy and paste it on the fstab file instead.

---

### Post by salman203 on 2009-02-27
> **iaculallad said:**
> Are you sure you copied the exact text I posted? Try to copy and paste it on the fstab file instead.
sure i followed exact steps. now i can access drive E but not drive C yet

---

### Post by salman203 on 2009-02-27
well i repeated the steps for drive c again and now it works fine. both drive c and E  contents are accessible now. i  m so much thankfull to u. thanks again

---

### Post by iaculallad on 2009-02-27
You're very much welcome. Go Ubuntu

---

