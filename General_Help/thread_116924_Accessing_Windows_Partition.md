---
title: "Accessing Windows Partition"
date: 2006-01-13
forum: General Help
---

### Post by pianoboy3333 on 2006-01-13
I have a Windows XP NTFS partition, how do I access it through ubuntu through the terminal so I can copy some files.

---

### Post by docmanny on 2006-01-13
You should have this line (substitute the partition for hda1) in /etc/fstab
> /dev/hda1  /win2k   ntfs defaults 0 0

Then in your terminal cd to /win2k and do what you have to do.
If you want to bypass fstab, use 
> sudo mount /dev/hda1 /win2k -t ntfs

---

### Post by pianoboy3333 on 2006-01-13
I think it's already mounted, I just can't access it, the partition, ubuntu calls it sda2, appears on the desktop, yet, I can't open it since i'm not root. Can't I just do some sort of 'cd /sda2' ?

---

### Post by stuporglue on 2006-01-13
See where it's mounted by:

$ mount
/dev/sda2 /media/foo
then cd to that place

$ sudo cd /media/foo
$ sudo ls 
$ sudo (etc. etc.)

---

### Post by pianoboy3333 on 2006-01-13
typing sudo cd /media/sda2

gives me the response command not found

---

### Post by aysiu on 2006-01-13
Post the output of these three commands, and we'll go from there: ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by pianoboy3333 on 2006-01-13
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2   *        6399       19451   104848222+   7  HPFS/NTFS
/dev/sda3            6080        6398     2562367+  82  Linux swap / Solaris

---

### Post by aysiu on 2006-01-13
What about these two commands? ```
cat /etc/fstab
df -h
```

---

### Post by pianoboy3333 on 2006-01-13
alex@dell9150:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
alex@dell9150:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G  3.0G   41G   7% /
tmpfs                 506M     0  506M   0% /dev/shm
/dev/sda2             100G  8.7G   92G   9% /media/sda2

---

### Post by aysiu on 2006-01-13
Follow these steps exactly as written in the exact order they're given: ```
sudo cp /etc/fstab /etc/fstab_backup
sudo umount /media/sda2
sudo mkdir /windows
sudo gedit /etc/fstab
``` Replace the **entire** contents of your /etc/fstab with this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda2 /windows ntfs nls=utf8,umask=0222 0 0
/dev/sda3 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
``` Save the file and exit Gedit. Then ```
sudo mount -a
cd /windows
ls
```

---

