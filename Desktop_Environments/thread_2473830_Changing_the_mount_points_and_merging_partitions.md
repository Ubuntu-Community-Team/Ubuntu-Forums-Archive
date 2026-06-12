---
title: "Changing the mount points and merging partitions"
date: 2022-04-14
forum: Desktop Environments
---

### Post by oygle on 2022-04-14
Have just done an install of 21.10, going from legacy to UEFI. It took several days, but at least there was good support - [https://ubuntuforums.org/showthread.php?t=2473650](https://ubuntuforums.org/showthread.php?t=2473650)

Haven't restored the data as yet. So, now that the partitions and access to them is not the same as previously, I need to change some mount points and merge 2 partitions. Here are the partitions:

```
sudo parted -l
```

> [sudo] password for ********: 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  2097kB  1049kB                                        bios_grub
 2      2097kB  540MB   538MB   fat32           EFI System Partition  boot, esp
 3      540MB   27.6GB  27.1GB  ext4
 4      27.6GB  33.0GB  5369MB  linux-swap(v1)                        swap, legacy_boot
 5      33.0GB  523GB   490GB   ext4                                  legacy_boot
 6      523GB   1000GB  477GB   ext4
 
and there is a KDE Partition manager screendump attached. I'm used to having just two mount points, one for "root" at / , and the other for all the data at /home , yet now it is quite different ..

```
mount | grep /dev/sda
```

> /dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda3 on /media/********/dd88117e-f1ba-41f8-83f5-7d4a0e627e4b type ext4 (rw,nosuid,nodev,relatime,errors=remount-ro,uhelper=udisks2)
/dev/sda5 on /media/********/8fd18908-340c-47a6-baf3-c0c65c5c226f type ext4 (rw,nosuid,nodev,relatime,errors=remount-ro,uhelper=udisks2)

To change this slightly, I assume I can just do it with a live usb, go into KDE Partition manager, and ..

1.  Merge /dev/sda5 and /dev/sda6 into on partion, by deleting /dev/sda6, then increase the size of /dev/sda5 with the unused space.
2.  Then make /dev/sda3 mount point as /
3.  Make /dev/sda5 mount point as /home

I see /dev/sda6 is currently mounted at /

The mount points for /dev/sda3 and /dev/sda5 are currently /media/*****/somebiglongname . Is it okay to change the mount points ?

---

### Post by oldfred on 2022-04-14
You cannot manage partition with little key icons. That shows mount.
I am more used to gparted, but very similar.

You cannot merge partitons.
If you want to change the / (root) partition you need to totally reinstall.

If you want to mount a partition as /home you can change it following these instructions.
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

---

### Post by oygle on 2022-04-15
@oldfred - By 'merge" I meant delete a partition, then increase the size of another partition by the effect of the unused space.

Thanks for the links and advice, you have been very helpful. Decided a reinstall was actually easier, and by using the "Try" first I can get the partitions as they were before; well almost.

```
sudo parted -l
```

> [sudo] password for ********: 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  2097kB  1049kB                                        bios_grub
 2      2097kB  540MB   538MB   fat32           EFI System Partition  boot, esp
 3      540MB   21.0GB  20.5GB  ext4
 7      21.0GB  26.1GB  5119MB  linux-swap(v1)                        swap
 4      26.1GB  1000GB  974GB   ext4
 
```
mount | grep /dev/sda
```

> /dev/sda3 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda4 on /home type ext4 (rw,relatime)

---

### Post by DuckHook on 2022-04-16
If you wish to have the flexibility of manipulating partitions post install, then you should consider installing into a LVM.

---

### Post by oygle on 2022-04-16
Thanks; I see there are a lot of articles about Ubuntu/LVM, so may have a read.  :)

---

### Post by DuckHook on 2022-04-16
If you parse through old forum threads, you will find lots of advice/hints/implementations from TheFu. Since installing my new system at the beginning of the year, I've used his strategy and the results have been great. I have far more flexibility than before and I can snapshot my OS before every upgrade, which has been awesome.

---

### Post by oygle on 2022-04-16
> **DuckHook said:**
> If you parse through old forum threads, you will find lots of advice/hints/implementations from TheFu. Since installing my new system at the beginning of the year, I've used his strategy and the results have been great. I have far more flexibility than before and I can snapshot my OS before every upgrade, which has been awesome.

Okay thanks. I see what you mean, just searched on **LVM** and **TheFu** and many detailed posts there. I like the idea of a snapshot prior to upgrade. My 'installation' notes involve backing up the data, plus  /etc , /usr/lib, /usr/local and /var to an external drive.

---

