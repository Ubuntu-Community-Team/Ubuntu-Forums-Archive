---
title: "Cannot mount my second Hard Disk"
date: 2009-01-30
forum: General Help
---

### Post by djtrickdog on 2009-01-30
Hello,

I dual boot Windows and Ubuntu off the same hard drive, and recently got a new 1.5TB hard drive. At the time, i was having some problems with my resolution in Ubuntu, so i formated the drive in Windows using NTFS. Now that i got my Video card problems fixed, I'm back on Ubuntu. When i go to  'Computer' in Ubuntu, i can see what I assume is my new drive labeled "SCSI Drive". I tried to right-click and mount it but nothing happens. When i double click to go into my drive and view its files, i get "UNABLE TO MOUNT LOCATION Can't Mount file" How do i mount this drive and get it working? Am i going to have to reformat the whole thing? :/ 

thanks alot!

---

### Post by taurus on 2009-01-30
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by djtrickdog on 2009-01-30
```
Disk /dev/sda: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x743f1dad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd05ed05e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14360   115346668+   7  HPFS/NTFS
/dev/sdb2           14361       19785    43576312+  83  Linux
/dev/sdb3           19786       20023     1911735    5  Extended
/dev/sdb5           19786       20023     1911703+  82  Linux swap / Solaris

Disk /dev/sdc: 507 MB, 507379712 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         983      495313+   6  FAT16
```



```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              41G  6.4G   33G  17% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M   36K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       41G  6.4G   33G  17% /home/ian/.gvfs
/dev/sdc1             484M  234M  251M  49% /media/disk
/dev/sdb1             111G   80G   31G  73% /media/disk-1

```

---

### Post by taurus on 2009-01-30
See if you can mount that drive, /dev/sda1, with

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
df -h
```

---

### Post by djtrickdog on 2009-01-30
> **taurus said:**
> See if you can mount that drive, /dev/sda1, with

```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
df -h
```

Hey it works! Thanks alot!

---

### Post by welder'75 on 2009-01-30
hi there! i'm new to this linux, spent the last 2 days tryin to get a dual boot system going with shared drives etc. i searched forums for answers and found that linux systems can't read ntfs formatted drives, like you need for microsoft.

linux uses ext3 formats, but both 'soft and linux will read FAT formats, so i have a spare storage partiton formatted in FAT so both linux and windows can read from it.

I used a program in windows, 'partition magic', a tool to partition and format drives in different format types. 

linux has a tool too, on desktop goto "system> administration> partition editor", you may have to download and install this tool, i needed to!

i have no idea on how to use the terminal or use commands yet, still getting my head around this linux system too!!

i hope this is of some help, good luck!

---

### Post by djtrickdog on 2009-01-30
Linux can read ntfs, because it works >_>

Sorry to bump this again, but how to i make it so when i reboot, it will always mount?

---

### Post by taurus on 2009-01-30
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.UTF-8   0   0
```
Save it and reboot.

---

