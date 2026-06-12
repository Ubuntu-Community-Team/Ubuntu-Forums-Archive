---
title: "problem with usb"
date: 2009-03-01
forum: General Help
---

### Post by nikhilneela on 2009-03-01
Hi friends,I would like to format my USB drive,but i cannot find any option like Format...nor i am able to delete the files manullay(because when i try to do so it says that some files cannot be removed(access denied))I am the only user of my computer...plz suggest a way to delete the files in the drive...PLZ PLZ PLZ

---

### Post by marsdend on 2009-03-01
> **nikhilneela said:**
> Hi friends,I would like to format my USB drive,but i cannot find any option like Format...nor i am able to delete the files manullay(because when i try to do so it says that some files cannot be removed(access denied))I am the only user of my computer...plz suggest a way to delete the files in the drive...PLZ PLZ PLZ

Hi, have you tried using Gparted from the Add / Remove to format the drive?

---

### Post by taurus on 2009-03-01
What filesystem is that USB drive and where did you mount it?

```
sudo fdisk -l
df -h
```

---

### Post by cariboo on 2009-03-01
The only way to format your usb device is to use gparted, it isn't installed by default, so you can use Add/Remove Programs or Synaptic Package Manager. Once installed go to System-->Administration-->Partition Editor.

To manage files on the device, press Alt-F2 and type:

```
gksu nautilus
```

This will run the file manager as root allowing you to copy, move and delete files on your device.

Jim

---

### Post by nikhilneela on 2009-03-01
nikhil@nikhil-desktop:~/Desktop$ sudo fdisk -l
[sudo] password for nikhil: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17251724

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/sda5            1913        3994    16723633+   7  HPFS/NTFS
/dev/sda6            4463        5737    10241406    7  HPFS/NTFS
/dev/sda7            5738        8287    20482843+   7  HPFS/NTFS
/dev/sda8            8288        9662    11044656   83  Linux
/dev/sda9            9663        9729      538146   82  Linux swap / Solaris

Disk /dev/sdb: 2020 MB, 2020539904 bytes
32 heads, 63 sectors/track, 1957 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x168912f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1957     1972624+   b  W95 FAT32




nikhil@nikhil-desktop:~/Desktop$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              11G  6.3G  3.8G  63% /
varrun                629M  172K  629M   1% /var/run
varlock               629M     0  629M   0% /var/lock
udev                  629M   68K  629M   1% /dev
devshm                629M  212K  628M   1% /dev/shm
lrm                   629M   39M  590M   7% /lib/modules/2.6.24-21-generic/volatile
/dev/sda5              16G  2.4G   14G  16% /media/Softwares
/dev/sda1              15G   11G  4.1G  73% /media/System
/dev/sda6             9.8G  2.8G  7.1G  28% /media/Studies
/dev/sda7              20G   16G  4.3G  79% /media/Entertainment
gvfs-fuse-daemon       11G  6.3G  3.8G  63% /home/nikhil/.gvfs
/dev/sdb1             1.9G  228M  1.7G  12% /media/disk

I got the above results

---

### Post by taurus on 2009-03-01
Remount /dev/sdb1.

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```
You should be able to delete files in /media/sdb1 now.

```
ls -la /media/sdb1
```

---

### Post by nikhilneela on 2009-03-01
I got like this....
nikhil@nikhil-desktop:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted

---

