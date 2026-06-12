---
title: "Disk Space Remaining Discrepancy"
date: 2006-08-05
forum: Desktop Environments
---

### Post by markus79 on 2006-08-05
Hi,

I'm having a problem with my hard disk. It is a 200G drive. When I log into Ubuntu I get a warning that my disk is 99% full. I know I am not using all this space.

According to Baobab and Nautilus I am using about 42GB of space for all files on /. Yet, other tools like Sysinfo say the disk is full and I am using the full 200GB.

Does anyone know what might be happening, or a tool to correct this? Hidden files,etc?

Thanks
Markus

---

### Post by dtfinch on 2006-08-05
Press ctrl-h in nautilus to view hidden files. I often back up my profiles from one system to another, and sometimes I've forgetten to empty the trash first, creating multiple copies of the files in my ".Trash" folder.

---

### Post by markus79 on 2006-08-06
What about external drives? I have two external drives... one is mounted as /media/EXTERNAL, the other /media/WD USB2.....  could this be part of the problem. These two drives alone have over 300GB... so it doesn't look like its figuring into my totals...

See screenshot attachment...

---

### Post by taurus on 2006-08-06
> **markus79 said:**
> What about external drives? I have two external drives... one is mounted as /media/EXTERNAL, the other /media/WD USB2.....  could this be part of the problem. These two drives alone have over 300GB... so it doesn't look like its figuring into my totals...

See screenshot attachment...
No screenshot attachment!  What are the outputs of these two comands from a terminal (Applications -> Accessories -> Terminal)?

```

df -h
sudo fdisk -l

```

---

### Post by markus79 on 2006-08-06
Screenshot should be there now...

mark@office:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2             177G  135G   42G  77% /
varrun                506M   88K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  160K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-23-386/volatile
/dev/hda1              75G   74G  1.2G  99% /tmp/disks-conf-hda1



mark@office:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1308    10506478+  82  Linux swap / Solaris
/dev/hdb2            1309       24319   184835857+  83  Linux

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    c  W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

---

