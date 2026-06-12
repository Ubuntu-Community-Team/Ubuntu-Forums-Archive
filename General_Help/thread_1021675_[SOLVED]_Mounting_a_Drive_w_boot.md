---
title: "[SOLVED] Mounting a Drive w/ boot"
date: 2008-12-25
forum: General Help
---

### Post by sirschuster on 2008-12-25
I would love to have my slave hard drive mounted by the time I hit my ubuntu desktop. How do I go by doing this?

Thanks.

---

### Post by albinootje on 2008-12-25
> **sirschuster said:**
> I would love to have my slave hard drive mounted by the time I hit my ubuntu desktop. How do I go by doing this?


Find out how it is mounted after you mount it, you can see that with the command :
```

mount

```
in a terminal.

After you've found that out, edit /etc/fstab, see here :
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by x1a4 on 2008-12-25
Hi,
Is the drive partitioned and formatted?  Please post the contents of your /etc/fstab file.  That's where you'll need to make the changes.

---

### Post by sirschuster on 2008-12-25
Ok i'll grab that in a sec. But yes, it is fully operational, i can click on the drive and it mounts, i just want it to be already mounted by the time i get into ubuntu, since i keep my music on the slave and it peeves of amarok when I forget to mount the drive before.

---

### Post by sirschuster on 2008-12-25
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c5d43c0b-4df6-4d4a-8611-97d2fdf2bf6a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=fb5de456-1756-4106-b04e-99527bcde05e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by sirschuster on 2008-12-25
My second drive is 'sdb', which obviously doesn't show up in the file I displayed.

---

### Post by albinootje on 2008-12-25
> **sirschuster said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c5d43c0b-4df6-4d4a-8611-97d2fdf2bf6a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=fb5de456-1756-4106-b04e-99527bcde05e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I don't see your slave drive mounted here.
Did you mount it ?
Can you post the output of :
```

sudo fdisk -l

```
Thanks.

---

### Post by sirschuster on 2008-12-25
Yup.

Here. it is and thanks for the help!

[I]sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x109b109a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/sda2            7013       14307    58597087+  83  Linux
/dev/sda3           14308       14946     5132767+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02c302c2

Device     Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12160    97675168+   7  HPFS/NTFS
[/I]

---

### Post by albinootje on 2008-12-25
> **sirschuster said:**
> 
Device     Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12160    97675168+   7  HPFS/NTFS
[/I]

Ok, thanks.
With NTFS partitions you can also do the following :
```

sudo apt-get install ntfs-config
sudo ntfs-config

```
That should let you choose the mount /dev/sdb1 for you, without having to edit /etc/fstab manually.
And, while using ntfs-config, it's probably better not to use spaces in the mountpoint name for /dev/sdb1 because that could cause problems later on!

---

### Post by sirschuster on 2008-12-25
Ok i did that, but sdb1 didnt appear on the ntfs-config, only my sda1 configuration.

---

### Post by albinootje on 2008-12-25
> **sirschuster said:**
> Ok i did that, but sdb1 didnt appear on the ntfs-config, only my sda1 configuration.

Hmm, okay.
Can you do the following :
```

sudo mkdir /media/sdb1-disk
sudo gedit /etc/fstab

```
Add this line :
/dev/sdb1 /media/sdb1-disk ntfs-3g defaults,locale=en_US.utf8 0 0
And save the /etc/fstab file, and type :
```

sudo mount -a

```

Change the two instances of "sdb1-disk" into e.g. datadisk if you prefer that.

If you get an error after the "sudo mount -a" about mounting read-only, then you have three options :
1) Boot into Windows and make sure you reboot your machine properly.
2) Install "ntfsprogs" and use the command
```
sudo ntfsfix /dev/sdb1
```
3) Mount the partition manually with : 
```
sudo mount /dev/sdb1 /media/sdb1-disk -t ntfs-3g -o force
```

---

### Post by sirschuster on 2008-12-25
Thank you so much, creating the new directory w/ the sudo mount -a did it. Yay!

---

### Post by Dumbestcrayon on 2008-12-26
Mark your thread as SOLVED please :)

---

