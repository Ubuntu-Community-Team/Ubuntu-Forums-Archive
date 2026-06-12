---
title: "UBUNTU 9.04 DOES NOT RECOGNIZE PARTITIONS NOR DVDs!"
date: 2009-05-19
forum: General Help
---

### Post by RsBrt on 2009-05-19
I managed to update from Ubuntu 8.04 to Ubuntu 8.10 but I lost the OpenOffice, Mozilla, etc. Later I updated to Ubuntu 9.04 but it says that it cannot mount the directories where I have my files. I had copied them in DVDs with Nero, but when trying to read them, Ubuntu says that they cannot be mounted, that DVDs DO NOT EXIST! 
In my opinion, UBUNTU 9.04 DOES NOT RECOGNIZE PARTITIONS NOR DVDs! According to the disc analyzer Ubuntu 9.04 uses only the space that the previous versions used. So, my partitions exist, but it does not see them, it does not recognize them, just like the DVDs. This is a problem of UBUNTU 9.04. I found a testdisk-6.11.3.Linux26.tar.bz2 but I do not know how to execute it. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).
PLEASE HEeeeeeeLP ME !!!
Sorry, I'm new with Linux! Thanks & regards!

---

### Post by taurus on 2009-05-19
Open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by RsBrt on 2009-05-19
robin@robin-desktop:~$ sudo fdisk -l
[sudo] password for robin: 

Disc /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/pista, 19929 cylinders
Unities = cylinders de 16065 * 512 = 8225280 bytes
Disk Identifier: 0x03420341

Disposit.   From    Begin      End      Blocks  Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       12764    61569112+   7  HPFS/NTFS
/dev/sda3           12765       19146    51263415    5  Extendida
/dev/sda4           19147       19929     6289447+   7  HPFS/NTFS
/dev/sda5           12765       18721    47849571   83  Linux
/dev/sda6           18722       19146     3413781   82  Linux swap / Solaris

robin@robin-desktop:~$ sudo blkid
/dev/sda1: UUID="0000000046899B23" LABEL="C" TYPE="ntfs" 
/dev/sda2: UUID="402C0F6F2C0F5EF2" LABEL="D" TYPE="ntfs" 
/dev/sda4: UUID="BA1C80591C801295" LABEL="E" TYPE="ntfs" 
/dev/sda5: UUID="2dfe38c5-719a-4ebb-a86a-5801cbc29bd2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="d06ed646-c2d8-4346-9792-72885477d712" 

robin@robin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2dfe38c5-719a-4ebb-a86a-5801cbc29bd2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=d06ed646-c2d8-4346-9792-72885477d712 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

robin@robin-desktop:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda5              46G  6,1G   37G  15% /
tmpfs                 1,5G     0  1,5G   0% /lib/init/rw
varrun                1,5G  236K  1,5G   1% /var/run
varlock               1,5G     0  1,5G   0% /var/lock
udev                  1,5G  152K  1,5G   1% /dev
tmpfs                 1,5G  100K  1,5G   1% /dev/shm
robin@robin-desktop:~$

What can I do to see my files? 
Tks & Rgds
):P

---

### Post by taurus on 2009-05-19
Are you talking about those ntfs partitions?  Install ntfs-config and use it to configure/mount those partitions.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by RsBrt on 2009-05-19
[FONT=Verdana, sans-serif][SIZE=2]Dear Taurus[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]I thank you sooo much![/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]I was near to a heart attack but now I feel happy because you helped me to recover my old files.[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]Only one more question: how could I read my DVDs? It gives Error in «gnome-mount» (File does not exist). 
May God bless you greatly!

[/SIZE][/FONT]:popcorn:

---

### Post by taurus on 2009-05-19
Maybe it's how you burnt the DVD using nero in windows.  Have you tried burning a DVD in Ubuntu and see if you can read from it?

---

### Post by retiredtechie on 2009-05-20
I had the same problem reading DVD backups I had made in Windows. After lots of searches I found a fix that worked for me.

Open a terminal and enter the following:

```
sudo gedit /etc/fstab
```

Look for a line similar to the following:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

and change it to:

/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0

Save fstab and reboot.  For some reason, exchanging the position of udf and iso9660 fixed it.

---

### Post by bacardiandwatermelon on 2009-05-20
This link may help with your dvd problem..
[http://ubuntuforums.org/showthread.php?t=1135129&highlight=ubuntu+dvd](http://ubuntuforums.org/showthread.php?t=1135129&highlight=ubuntu+dvd)

---

### Post by RsBrt on 2009-05-20
[FONT=Verdana, sans-serif][SIZE=2]The main problem is that Ubuntu DOES NOT RECOGNIZE OTHER OPERATING SYSTEMS ERROR 11.[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]So, it does not recognize any legal programs in the PC, CDs or DVDs![/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Help please![/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]Tnks & Rgds![/SIZE][/FONT]

---

### Post by RsBrt on 2009-05-20
[FONT=Verdana, sans-serif][SIZE=2]THANKS A LOT![/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]I solved my problem typing in a terminal[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]sudo gedit /etc/fstab[/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=2]as retiredtechie posted.[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]I didn't change anything, rebooted and I found my other operating system OK![/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]
Your are really great.[/SIZE][/FONT] [FONT=Verdana, sans-serif][SIZE=2]HATS OFF to the Ubuntu FORUM Community!

[/SIZE][/FONT]):P

---

