---
title: "File Permissions"
date: 2009-01-29
forum: General Help
---

### Post by kneewax on 2009-01-29
Hey folks,

I seem to have mucked up the permissions on my data FAT32 partition.  Not sure what happened, but files in some of the folders and sub-directories are set to read only.

Is there away I can reset the permissions to give me full access to the folders, sub folders and files (i.e the entire tree) on the partition sda2?

Realise this is a probably a simple question, but I have never had to do this before!:confused:

---

### Post by taurus on 2009-01-29
How did you mount your /dev/sda2 (fat32/vfat)?  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by kneewax on 2009-01-29
```

-$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3833069c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19534016   83  Linux
/dev/sda3            2433       19457   136753312+   5  Extended
/dev/sda5           19203       19457     2048256   82  Linux swap / Solaris
/dev/sda6            7774       19202    91803411    b  W95 FAT32
/dev/sda7            2433        7773    42901519+  83  Linux

Partition table entries are not in disk order


-$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
UUID=3183daa5-db56-45a0-9240-44ae33a68487 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda6       /media/sda2     vfat    utf8,umask=007,gid=46 0       1
UUID=d4fed0c5-7e82-4171-9aac-577247230fad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda7 /home ext3 nodev,nosuid 0 2



-$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  7.5G   10G  44% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  212K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.7M  1.5G   1% /dev
tmpfs                 1.5G  356K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6              88G   17G   71G  20% /media/sda2
/dev/sda7              41G   15G   24G  39% /home

```
 There you go! sda6 is mounted /media/sda2 for legacy reasons.

---

### Post by taurus on 2009-01-29
Try remounting it.

```
sudo umount /media/sda2
sudo mount -t vfat /dev/sda6 /media/sda2 -o umask=000
df -h
```

p.s.  Is Ubuntu the only OS on that machine?

---

