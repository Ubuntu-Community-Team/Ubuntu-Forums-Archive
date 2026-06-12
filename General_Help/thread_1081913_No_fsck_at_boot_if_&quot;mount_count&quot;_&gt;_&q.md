---
title: "No fsck at boot if &quot;mount count&quot; &gt; &quot;max mount count&quot;"
date: 2009-02-27
forum: General Help
---

### Post by akssoon on 2009-02-27
Hi

I have a Windows XP/Ubuntu Hardy Heron system running on my Laptop (Acer Travelmate 290 series). My partition setup looks like this:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        5175    20595330   83  Linux
/dev/sda3            5176        5345     1365525   82  Linux swap / Solaris
/dev/sda4            5346       14593    74284560   83  Linux
```

/dev/sda1 --> Windows XP (NTFS)
/dev/sda2 --> Ubuntu / (Ext3)
/dev/sda4 --> "data" partition (Ext3)

Now the thing is I mount my "data" partition with both operation systems. In ubuntu it is mounted as an ext3 partition at /home/myusername/data, in Windows XP it is mounted as an ext2 partition as drive "D:\". Mounting under windows is done via [http://www.fs-driver.org/]("http://www.fs-driver.org/").
This mounting with both operation systems more often than not results in the mount count of /dev/sda4 being higher than the max mount count. This however doesn't trigger a fsck at boot time (when booting ubuntu).

**Is that normal behaviour, or a bug of the boot script not checking if mount count equal or greater than max mount count?**
Or maybe I changed something that I don't know of anymore?

What I currently do is boot into ubuntu once in a while and do a
```
sudo tune2fs -l /dev/sda4 | grep -i "mount count"
```
and if it outputs something like it does right now
```
Mount count:              83
Maximum mount count:      30
```
I do do a
```
sudo e2fsck -p /dev/sdaX
```
AFTER I unmounted the filesystem.

---

### Post by iaculallad on 2009-02-27
Post your /etc/fstab file.

---

### Post by akssoon on 2009-03-03
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1b2828f9-cbb7-4f14-9261-9a43ded30b51 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3
UUID=bfba9c07-742a-4e02-aa5e-5112f2cf177c none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sda4
UUID=04a664f7-cbe7-4b90-a9c8-f1b61916b6e4 /home/akssoon/data ext3 relatime,errors=remount-ro 0 2
```
I appreciate the help...thx!

---

### Post by dcstar on 2009-03-03
> **akssoon said:**
> 
.........
Now the thing is I mount my "data" partition with both operation systems. In ubuntu it is mounted as an ext3 partition at /home/myusername/data, in Windows XP it is mounted as an ext2 partition as drive "D:\". Mounting under windows is done via [http://www.fs-driver.org/]("http://www.fs-driver.org/").
This mounting with both operation systems more often than not results in the mount count of /dev/sda4 being higher than the max mount count. This however doesn't trigger a fsck at boot time (when booting ubuntu).

**Is that normal behaviour, or a bug of the boot script not checking if mount count equal or greater than max mount count?**
........

I suspect it is a bug, but you can also set the partition to fsck after "X" period (default seems to be 6 months), so you could set it to check every 7 days (for instance):
```
sudo tune2fs /dev/sda4 -i1w
```
That may get around the issue and help with keeping the partition integrity ok.

---

### Post by Slim Odds on 2009-03-03
> **dcstar said:**
> I suspect it is a bug, but you can also set the partition to fsck after "X" period, so you could set it to check every 7 days (for instance):
```
sudo tune2fs /dev/sda4 -i1w
```

I agree.... I turn the mount count limit off on my partitions and just use the date/time ones. Ext3 is pretty robust and if you need to, you can check it manually.

---

### Post by akssoon on 2009-03-05
Well then I'll go with that ^^

---

