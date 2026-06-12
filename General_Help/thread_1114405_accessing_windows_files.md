---
title: "accessing windows files"
date: 2009-04-02
forum: General Help
---

### Post by Bill Yoder on 2009-04-02
I've got most of Ubuntu running, but seem to have a weird problem with each step. Hopefully this will be the last major one. 

It would help if I were able to access my windows files in Ubuntu but I can only get some of them.

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa17da17d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    68356574    34178256    c  W95 FAT32 (LBA)
/dev/sda2        68356575   240107489    85875457+   f  W95 Ext'd (LBA)
/dev/sda5        68356638   117194174    24418768+   b  W95 FAT32
/dev/sda6       185550813   240107489    27278338+   b  W95 FAT32
/dev/sda7       117194238   182642984    32724373+  83  Linux
/dev/sda8       182643048   185550749     1453851   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders, total 16514064 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x03480347

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    16434494     8217216    b  W95 FAT32
 Prior to Linux install my primary drive had four partitions, all FAT32.
sda appears to be my primary master disk.
sdb is secondary drive, also FAT32 and apparently bootable. It was designated D: and labeled BACKUPS. It appears in Nautilus and files are available.
sda1 and 2 appear to be original C: drive labeled ROOT. Is not in Nautilus and cannot be mounted.
sda5 was E: labeled DATA, not in Nautilus. This is the drive I really want to access.
sda6 was G: labeled MISC, same as above but not needed here.
sda7 and 8 are obviously available.

disk partitions

bill@mine:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              31G  3.8G   26G  13% /
varrun                490M   96K  490M   1% /var/run
varlock               490M  4.0K  490M   1% /var/lock
udev                  490M   76K  490M   1% /dev
devshm                490M   52K  490M   1% /dev/shm
lrm                   490M   39M  451M   8% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       31G  3.8G   26G  13% /home/bill/.gvfs
/dev/scd1             580M  580M     0 100% /media/cdrom1

How can I access sda5 from Ubuntu?

---

### Post by taurus on 2009-04-02
```
sudo mkdir /media/sda5
sudo mount -t vfat /dev/sda5 /media/sda5 -o umask=000
df -h
```

---

### Post by Bill Yoder on 2009-04-06
Problem solved!

I got my documents copied into Ubuntu. I am still puzzled as to why my second drive showed up automatically and can be accessed like any directory, while the logical partition must be mounted eaxh time I boot Ubuntu. At least now I know how to do it and don't need to do it that often.

I did it wrong about ten times, began to think I am an idiot. Did it right once, I'm a genius again. Thanks for the help.

---

### Post by taurus on 2009-04-06
If you want to mount /dev/sda5 automatically each time you boot Ubuntu, you can add an entry in /etc/fstab for it.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000   0   0
```
Save it and reboot.

---

