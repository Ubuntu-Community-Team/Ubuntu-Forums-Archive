---
title: "Mounting my NTFS partition"
date: 2006-06-27
forum: Desktop Environments
---

### Post by MikeMLP on 2006-06-27
I installed using the alternate CD
The only way to procede with the install was to set the mountpoint to "none" for my windows partition, as it would come up with an error message if I tried to set a mountpoint. 

So now, I am trying to set up a mountpoint from within my working install.

I've tried following the instructions here:
[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")

fdisk -l shows all partitions as it should, but...
fstab does not have a /dev/hda1 entry (my NTFS partition)

I tried to edit it manually, just typing in the correct info, but it says that I have an error on "line 11," the line that I edited.

Is there a proper way to add my NTFS partition as I would like to?

Thanks!

---

### Post by aysiu on 2006-06-27
Well, post the output here of this command ```
cat /etc/fstab
``` and we'll see what error is in line 11.

---

### Post by MikeMLP on 2006-06-27
perhaps I should have been more clear.  Line 11 included text that I manually tried to put in myself in order to get the drive to mount.  I have since deleted that line.  Regardless, I will now post both.  And for future reference, how does one enter code into the forums?

---

### Post by MikeMLP on 2006-06-27
results of sudo fdisk -l:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1      109714    55295698+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2          145621      155055     4755240   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/hda3          109714      132680    11574832+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda4          132680      145605     6514357+   b  W95 FAT32
Partition 4 does not end on cylinder boundary.
/dev/hda5          109714      130640    10546641   83  Linux
/dev/hda6          130640      132680     1028128+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 257 MB, 257474560 bytes
65 heads, 32 sectors/track, 241 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         242      251423+   4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 64, 32) logical=(241, 49, 31)

---

### Post by MikeMLP on 2006-06-27
results of cat /etc /fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /fat            vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda2       /ibm_restore    vfat    defaults,utf8,umask=007,gid=46 0       1/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


***
dev/hda1 is not listed here, presumably because I set mountpoint to "none" during the install - it was the only way that the installer would allow me to continue.

---

### Post by aysiu on 2006-06-27
To address your issues one by one:

1. Code should be bracketed by these two tags (take out the extra spaces): [c o d e] *actual code you're pasting in* [ / c o d e]

2. That's weird. When I did an install with the Desktop CD, the installer forced me to mount my Windows partition. You were forced to *not* mount it? Well, I don't like being forced either way, but that's strange.

3. Your /etc/fstab line should be ```
/dev/hda1 /mountpointname ntfs nls=utf8,umask=0222 0 0
``` and you can add it if it isn't there. This assumes, of course, that you created the folder already: ```
sudo mkdir /mountpointname
``` And after you finish editing the /etc/fstab, you should remount the partition ```
sudo umount /dev/hda1
sudo mount -a
```

---

### Post by MikeMLP on 2006-06-27
Thanks! worked like a charm!

and just to clear up one other bit:
> I installed using the alternate CD
And it would not mount my NTFS partition to /windows (or any other directory so I had to just tell it not to make a mount point.

---

### Post by aysiu on 2006-06-27
That's weird. Yeah, I used the Desktop CD.

I was actually kind of pissed that it made me mount the partition... I just unmounted it after installation, though.

---

