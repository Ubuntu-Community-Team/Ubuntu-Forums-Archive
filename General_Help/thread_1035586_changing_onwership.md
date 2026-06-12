---
title: "changing onwership"
date: 2009-01-09
forum: General Help
---

### Post by kantu on 2009-01-09
i was downloading a torrent file. the file was on a mounted partition, till recently the permissions were not root , and the system did a disk check during boot up and from then all the mounted partitions ownership has been changed to root , so now i am not able to continue the torrents or modify(delete or cut) it :(
How can i change it back ?

---

### Post by taurus on 2009-01-09
Which partition is that?

Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by kantu on 2009-01-09
srikanth@srikanth-desktop:~$ sudo fdisk -l
[sudo] password for srikanth: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7b5c7b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        4865    39070080    f  W95 Ext'd (LBA)
/dev/sda5               2        2411    19358293+   7  HPFS/NTFS
/dev/sda6            2412        2910     4008186    7  HPFS/NTFS
/dev/sda7            4217        4865     5213061    7  HPFS/NTFS
/dev/sda8            2911        4154     9992398+  83  Linux
/dev/sda9            4155        4216      497983+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551       16573   112639747+   f  W95 Ext'd (LBA)
/dev/sdb3           16574       16598      200812+  83  Linux
/dev/sdb4           16599       19457    22964917+  8e  Linux LVM
/dev/sdb5            2551        6401    30933126    7  HPFS/NTFS
/dev/sdb6            6402        8924    20265966    7  HPFS/NTFS
/dev/sdb7            8925       11474    20482843+   7  HPFS/NTFS
/dev/sdb8           11475       15678    33768598+   7  HPFS/NTFS
/dev/sdb9           15679       16573     7189056    7  HPFS/NTFS
srikanth@srikanth-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda8 :
UUID=66b818cf-fe18-4509-a399-e2a7a960c4b1	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb6 :
UUID=8E34A2A734A2922F	/media/Downloads	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sdb5 :
UUID=F604443B044400DB	/media/Games	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sdb9 :
UUID=38A0EF1CA0EEDEFE	/media/Solaris	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sdb3 :
UUID=63fafc88-12e5-4dc0-b14a-af0f34e58784	/media/boot	ext3	defaults0	2
#Entry for /dev/mapper/VolGroup00-LogVol00 :
UUID=92e7559a-5f0d-401c-a2d6-0946d5a56ede	/media/dm-0	ext3	defaults0	2
#Entry for /dev/sdb8 :
UUID=BE9866DA986690A7	/media/misc	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sdb7 :
UUID=AE70534670531505	/media/music	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sdb1 :
UUID=500C1D7D0C1D5F72	/media/sdb1	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sda5 :
UUID=F2685B34685AF6B7	/media/*	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sda6 :
UUID=1644386944384DAD	/media/*_	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sda7 :
UUID=BCB8A6A1B8A65A22	/media/*__	ntfs	defaults,nls=utf8,umask=0222	00
#Entry for /dev/sda9 :
UUID=dfb95a92-9352-42db-8498-0fed3d326868	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


srikanth@srikanth-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             9.4G  5.9G  3.1G  67% /
tmpfs                1011M     0 1011M   0% /lib/init/rw
varrun               1011M  108K 1011M   1% /var/run
varlock              1011M     0 1011M   0% /var/lock
udev                 1011M  2.8M 1009M   1% /dev
tmpfs                1011M  292K 1011M   1% /dev/shm
lrm                  1011M  2.0M 1009M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb6              20G   17G  3.3G  83% /media/Downloads
/dev/sdb5              30G   27G  3.0G  91% /media/Games
/dev/sdb9             6.9G  4.4G  2.6G  63% /media/Solaris
/dev/sdb3             190M   21M  160M  12% /media/boot
/dev/mapper/VolGroup00-LogVol00
                       18G   12G  5.0G  71% /media/dm-0
/dev/sdb8              33G   31G  2.1G  94% /media/misc
/dev/sdb7              20G  9.9G  9.7G  51% /media/music
/dev/sdb1              20G   17G  2.8G  87% /media/sdb1
/dev/sda5              19G   13G  6.2G  67% /media/*
/dev/sda6             3.9G   74M  3.8G   2% /media/*_
/dev/sda7             5.0G   30M  5.0G   1% /media/*__
/dev/scd0             4.3G  4.3G     0 100% /media/cdrom0
srikanth@srikanth-desktop:~$ 


i have ubuntu 8.10
well i got the torrents downloading i just did 
sudo azureus (so that the program has permissions)
but still i couldnt change permissions for the partitions

---

