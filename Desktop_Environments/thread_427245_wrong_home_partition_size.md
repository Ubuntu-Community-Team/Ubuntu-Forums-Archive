---
title: "wrong /home partition size"
date: 2007-04-29
forum: Desktop Environments
---

### Post by Ozeuss on 2007-04-29
Hi everyone.
I've used edgy for a while and then did a clean install of feisty (and mounting the old /home). I moved partitions around for a bit (shrinking the NTFS partition to mininum, making more room for /home) and now it seems  that /home occupies more space than it should. It's size is supposed to be 17.5 gigs, and only 6.6 used.
Gparted shows the right size, but it says 15 gigs are occupied.
on system monitor i see only 10 gigs.
nautilus' properties tab on my user folder shows only 6.6 gig are used
my fstab output:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4243a620-76da-4a57-bc95-7b0671b8bed5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
# UUID=1a1e3390-112c-496a-ba84-78c7f075beb6 /home           ext3    defaults        0       2
/dev/sda5 /home ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=F63CC0453CBFFF1D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
# UUID=5675a03a-fe8c-49ab-a162-911a9c0caeeb none            swap    sw              0       0
/dev/sda6 none swap sw 0 0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
as you can see at first i thought it might be a uuid problem, but no...

fdisk -l output:
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1288    10345828+   7  HPFS/NTFS
/dev/sda2            2423        4864    19615365    f  W95 Ext'd (LBA)
/dev/sda3            1289        2422     9108855   83  Linux
/dev/sda5            2423        4712    18394393+  83  Linux
/dev/sda6            4713        4864     1220908+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Thanks in advance!

---

### Post by taurus on 2007-04-29
What's the output of this command from a terminal?

```
df -h
```

---

### Post by Ozeuss on 2007-04-29
thanks for the reply Taurus
```
/dev/sda3             8.6G  3.7G  4.5G  46% /
varrun                252M  112K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  128K  252M   1% /proc/bus/usb
udev                  252M  128K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile
/dev/sda5              11G  8.1G  1.6G  85% /home
/dev/sda1             9.9G  7.3G  2.6G  74% /media/sda1

```
/home is sda5, and shows 11g. when i booted from the live cd, it mounted the partition as 17.5G, but also showed only 1.6 availabe.
I also ran fsck (through the live cd) and it didn't find anything.

---

### Post by Ozeuss on 2007-04-29
Anyone?

---

### Post by mlind on 2007-04-29
If you have resized ext2/3 partition, you'll need to resize the filesystem inside too.
Have you tried
```

sudo init 1
umount /home
fsck -f /dev/sda5
**resize2fs /dev/sda5**
mount /home
init 2

```

---

### Post by Ozeuss on 2007-04-29
hey mlind,
i ran fsck on that partition, which came out clean, but not resize2fs. i'll try it, thanks.

---

### Post by Ozeuss on 2007-04-29
Great!
everything seems to be ok- right size is showing both on df and in gparted.
thanks alot!

---

