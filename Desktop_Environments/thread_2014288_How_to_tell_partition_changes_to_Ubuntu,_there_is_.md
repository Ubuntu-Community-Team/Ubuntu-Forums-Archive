---
title: "How to tell partition changes to Ubuntu, there is mounting problem during the boot"
date: 2012-07-01
forum: Desktop Environments
---

### Post by taner on 2012-07-01
Hi,

I have installed Ubuntu with an extra FAT 32 partition but I have chosed its mount point to be /windows 
and yesterday I have booted my pc with Active@ boot disk and formatted the partition to NTFS. Now it is without mount point (this is what I want)

Now when I am booting, it stops and ubuntu tells me that it can not mount /windows partition and I have to press S button to skip mounting. When the boot is complate I can mount and use the NTFS partition.

How can I tell the partition changes to ubuntu?


sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62926604    31463271    7  HPFS/NTFS/exFAT
/dev/sda2        62926846   312580095   124826625    5  Extended
/dev/sda5        62926848   219176959    78125056    7  HPFS/NTFS/exFAT
/dev/sda6       219179008   277770239    29295616   83  Linux
/dev/sda7       277772288   281769983     1998848   82  Linux swap / Solaris
/dev/sda8       281772032   312580095    15404032   83  Linux

it is the sda5

sudo gedit /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a6cb7d30-b0ca-4a90-a397-5f2630578f33 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=c0c9d1bf-8aae-4777-8789-2879be86a59e /home           ext4    defaults        0       2
# /windows was on /dev/sda5 during installation
UUID=2505-DD13  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda7 during installation
UUID=c9e17be9-a2de-4e44-8fc8-e3d57934d102 none            swap    sw              0       0

---

### Post by rai4shu2 on 2012-07-01
Change the line in fstab to:

```
/dev/sda5 /windows ntfs    defaults,umask=007,gid=46 0       0
```

Then change "/dev/sda5" when you can to the new UUID, which you can discover with:

```
ls -o /dev/disk/by-uuid/
```

---

### Post by taner on 2012-07-01
Thank you for the quick response rai4shu2,

I changed the line as you told me,

UUID=8640E18C40E18373  /windows   ntfs  defaults,umask=007,gid=46   0    0


The mounting question is not appering during the boot but now I can not see this partition and can not mount and use it in Ubuntu?

---

### Post by rai4shu2 on 2012-07-01
Problem? Just go to /windows in Nautilus or whatever file manager you use.

---

