---
title: "ummountig hdb"
date: 2006-09-26
forum: Desktop Environments
---

### Post by LORD_PoLvO on 2006-09-26
hey people i have a windows aprtioned drive that i want to format and then make ext3 but i am having problems with it first of all i am having trouble with this:

```
daniel@daniel-desktop:~$ fdisk /dev/hdb

Unable to open /dev/hdb
```

so not really knowing much about migrating devices i tried to format with qtpartedand then i tried this

```
daniel@daniel-desktop:~$ sudo mkfs -t ext3 /dev/hdb
mke2fs 1.38 (30-Jun-2005)
/dev/hdb is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/hdb is apparently in use by the system; will not make a filesystem here!
```

now i dont rewally know much about what to do with this im new to setting up hardrives in ubuntu so could anyone please help me with this pelase?/

much apreciated if you can thnx :D

---

### Post by kidders on 2006-09-26
Hi there,

Technically, you can't format a disk per se ... you'll probably want to create a partition on it and format that.

First step is to make sure your system isn't using it though ... check that "mount | grep /dev/hdb" doesn't return anything.

---

### Post by rogier.de.groot on 2006-09-26
First of all, "fdisk /dev/hdb" should be "sudo fdisk /dev/hdb". What I'd do is "sudo gedit /etc/fstab" and remove the line for you windows partition, if there is one. If there is, just reboot after removing the line (not the best solution, granted).
Then, with fdisk make a partition (eg. /dev/hdb1) and use mkfs like you did before.

---

### Post by LORD_PoLvO on 2006-09-26
k thnx i will try that now and btw i did mount | grep /dev/hdb and it did not return anything thats why i was confused but i will try to fix fstab now... :D

---

### Post by LORD_PoLvO on 2006-09-26
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


thats my fstab my primary master (hda) is there but not primary salve (hdb) so i will try to format and partion now :D

---

