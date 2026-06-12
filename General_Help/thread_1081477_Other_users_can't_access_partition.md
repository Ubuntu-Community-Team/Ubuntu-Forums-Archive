---
title: "Other users can't access partition"
date: 2009-02-26
forum: General Help
---

### Post by platinumxo on 2009-02-26
Okay im new to linux. Downloaded Ubuntu 8.10.  I think I have gnome.  How do you check it anyway? Anyway...

I added a _new user_ so whoever want to can use Ubuntu :D without them snooping around mine.

Here's the issue.  
I created a partition NTFS format to seperate and share all my music and other files so the other user can use it too.  *under _new user_* it can't view the partition. Here's what it says: 

The folder contents could not be displayed
You do not have the permissions neccessary to view the contents of "Files".

I have no idea on how to give _new user_ the permission.  I'm still looking and playing around on this new OS.  If someone can point me how please tell me.  Thanks in advance.

---

### Post by platinumxo on 2009-02-26
bump bump bump... these thread goes quick hehe

---

### Post by taurus on 2009-02-26
How do you mount that share partition?  Do you have an entry in /etc/fstab to have it mount automatically each time you boot?

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by platinumxo on 2009-02-26
ok i typed all on codes. i can't read those outputs hahaha

```
mervin@mervin-laptop:~$ sudo fdisk -1
[sudo] password for mervin: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
mervin@mervin-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6b69e0d8-cf85-49b1-ba10-a9779ad4a357 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b8e2b384-3a8c-4eb7-9e66-56f0504ae3aa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
mervin@mervin-laptop:~$ df-h
bash: df-h: command not found
mervin@mervin-laptop:~$
```

---

### Post by taurus on 2009-02-26
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That should be a lower case letter L, not number 1.

```
df -h
```
There is a space between df and -h.

---

### Post by platinumxo on 2009-02-26
oops wrong again: edited
```
mervin@mervin-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5973cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546   83  Linux
/dev/sda2            9378        9729     2827440    5  Extended
/dev/sda3            3188        9377    49721175    b  W95 FAT32
/dev/sda5            9378        9729     2827408+  82  Linux swap / Solaris

Partition table entries are not in disk order
mervin@mervin-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              25G  2.8G   21G  13% /
tmpfs                 473M     0  473M   0% /lib/init/rw
varrun                473M  128K  473M   1% /var/run
varlock               473M     0  473M   0% /var/lock
udev                  473M  2.7M  470M   1% /dev
tmpfs                 473M  1.3M  472M   1% /dev/shm
lrm                   473M  2.0M  471M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3              48G  4.9G   43G  11% /media/Files
```


thanks for looking into

---

### Post by platinumxo on 2009-02-26
okay i'll be gone for 4.5 hours.  Please help me get Linux all set up :D

---

### Post by taurus on 2009-02-26
I assume you want to have /dev/sda3 (fat32/vfat filesystem) mounted automatically each time you boot.  Therefore, you need to create an entry in /etc/fstab for it.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda3   /media/Files   vfat   iocharset=utf8,umask=000  0  0
```
Save it and reboot.  Once you've logged back in with your username and password, see if /dev/sda3 appears on /media/Files now.

```
df -h
```

---

### Post by platinumxo on 2009-02-27
```
mervin@mervin-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              25G  2.8G   21G  13% /
tmpfs                 473M     0  473M   0% /lib/init/rw
varrun                473M  104K  473M   1% /var/run
varlock               473M     0  473M   0% /var/lock
udev                  473M  2.7M  470M   1% /dev
tmpfs                 473M  436K  473M   1% /dev/shm
lrm                   473M  2.0M  471M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3              48G  4.9G   43G  11% /media/Files
```

It worked! Thank you very much for all your help.  Now I need to try themes.  Loving this Ubuntu hahhaha.

---

