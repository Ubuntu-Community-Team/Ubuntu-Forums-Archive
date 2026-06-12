---
title: "EXT3-fs error (device hda1) in start_transaction: Readonly filesystem"
date: 2005-04-02
forum: Desktop Environments
---

### Post by manatlan on 2005-04-02
Since some days (2-3 days) ...

my ubuntu hoary up-to-date (2.8.10 i686) is really strange
The first boot of the day, it works ... and 5 to 10 minutes later ...
Nothing works ! (it's not a application that i launch)

when i go to a console .... i've got this :
EXT3-fs error (device hda1) in start_transaction: Readonly filesystem
EXT3-fs error (device hda1) in start_transaction: Readonly filesystem
EXT3-fs error (device hda1) in start_transaction: Readonly filesystem
EXT3-fs error (device hda1) in start_transaction: Readonly filesystem
...

and i can't do nothing ... and must to reboot ... after that, it works better
it s a great problem to use ubuntu forever !

how can i resolve this big trouble ?!?

---

### Post by askreet on 2005-04-02
Please post the content of /etc/fstab as well as the output of fdisk -l /dev/hda

Thanks,
 Skreet

---

### Post by manatlan on 2005-04-03
Here is my fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hdb1       /mnt/mdk        ext3    defaults,errors=remount-ro 0       1
/dev/hdb5 	/mnt/mdkhome	ext3 defaults 1 2
/dev/hdb7 	/mnt/win_c2	vfat umask=022,iocharset=utf8,uid=1000,gid=1000,codepage=850,defaults 0 0
/dev/hda5 	/mnt/win_d	vfat umask=022,iocharset=utf8,uid=1000,gid=1000,codepage=850,defaults 0 0
/dev/hda2 	/mnt/win_e	ntfs umask=022,nls=utf8,uid=1000,gid=1000,ro 0 0
/dev/hda4 	/mnt/win_gb	vfat umask=022,iocharset=utf8,codepage=850 0 0
#iocharset=iso8859-15

i just had see, the "remount readonly on error" on my "/" (hda1) ...
i think it's that ... but what are the errors ?!?


here is my fdisk :
Disque /dev/hda: 122.9 Go, 122942324736 octets
255 têtes, 63 secteurs/piste, 14946 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1               1         509     4088511   83  Linux
/dev/hda2             519        2811    18418522+   7  HPFS/NTFS
/dev/hda3            2812       14946    97474387+   f  W95 Etendu (LBA)
/dev/hda4             510         518       72292+  16  Hidden FAT16
/dev/hda5            2812       14946    97474356    b  W95 FAT32


but now, it's R/W, because, like all days, my first boot made it readonly, and i had rebooted again ... and works well
but all days it's the same problem !!!!

---

### Post by manatlan on 2005-04-04
finally ... this morning
my ubuntu doesn't want to boot ... "too many errors on the filesystem"
i booted a mandrake and made a fsck /dev/hda1 ..
there were a lot of errors ... all were repaired

and now, it boot normally again !

---

### Post by waseda on 2006-08-31
I meet the same error, and here is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/hda6 /               ext3    defaults,errors=remount-ro 0       0
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

seems that everytime i login i have to mount -o remount,rw / if not all things become read-only. I also cannot reboot or shutdown the machine, there're many error:
EXT3-fs error (device hda1) in start_transaction: Readonly filesystem
EXT3-fs error (device hda1) in start_transaction: Readonly filesystem

Please help!

---

### Post by waseda on 2006-08-31
And here

nmnguyet@ubuntu:~$ sudo fdisk -l /dev/hda
Password:
sudo: Can't open /var/run/sudo/nmnguyet/3: Read-only file system
postdrop: warning: mail_queue_enter: create file maildrop/672810.11472: Read-only file system

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           8       64228+  83  Linux
/dev/hda2               9        4870    39054015    5  Extended
/dev/hda5               9         130      979933+  82  Linux swap / Solaris
/dev/hda6             131        4870    38074018+  83  Linux
nmnguyet@ubuntu:~$ postdrop: warning: mail_queue_enter: create file maildrop/672810.11472: Read-only file system

---

