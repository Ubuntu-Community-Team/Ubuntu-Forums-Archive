---
title: "Trouble mounting secondary partition."
date: 2009-03-13
forum: General Help
---

### Post by bobmatino17 on 2009-03-13
well i reacently rembered i had about 17 gigs left on my hdd, so i used gparted to create a partition so that space could be used. however, it cant auto-mount and i cant just go and click on it to mount it. i tried modifying fstab, but it was different from the last one i worked on (gentoo, getting it to accept flash drives.)anyone know how to get it to auto-mount?

---

### Post by taurus on 2009-03-13
Which partition you want to mount and where do you want to mount it to, mount point?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by bobmatino17 on 2009-03-13
i want to mount /dev/sda3 to /media/disk.

---

### Post by bobmatino17 on 2009-03-13
here is the output of the commands
```
tuxiscool@tuxiscool-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0741425b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12158    97659103+  83  Linux
/dev/sda2           12159       12401     1951897+   5  Extended
/dev/sda3           12402       14593    17607240   83  Linux
/dev/sda5           12159       12401     1951866   82  Linux swap / Solaris
tuxiscool@tuxiscool-desktop:~$ sudo blkid
/dev/sda1: UUID="4759b464-2d7c-4392-b67b-332f84356b5c" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="42e73ac1-3784-405e-b844-c0feb1cf811e" 
/dev/sda3: UUID="19192a81-641b-454a-ac23-c0f63c193409" TYPE="ext4" 
tuxiscool@tuxiscool-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4759b464-2d7c-4392-b67b-332f84356b5c /               ext4    relatime,errors=remount-ro 0       1
# none was on /dev/sda5 during installation
UUID=42e73ac1-3784-405e-b844-c0feb1cf811e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#lines below added by Donald G. Wilson III
#/dev/sda3	/media/sda3	ext4	auto		0	0
tuxiscool@tuxiscool-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              92G   17G   71G  20% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M  224K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   80K  502M   1% /dev
tmpfs                 502M  248K  502M   1% /dev/shm
lrm                   502M  2.0M  500M   1% /lib/modules/2.6.28-6-generic/volatile
tuxiscool@tuxiscool-desktop:~$ 

```

---

### Post by taurus on 2009-03-13
I guess you can edit /etc/fstab and add this line to the end of it.

```
/dev/sda3   /media/disk   ext4   defaults   0   2
```
Save it.  Then, create the new mount point and mount it.

```
sudo mkdir /media/disk
sudo mount -a
df -h
```

Or you can use **UUID=19192a81-641b-454a-ac23-c0f63c193409** instead of **/dev/sda3** in /etc/fstab.

---

### Post by bobmatino17 on 2009-03-13
every thing went well (changed my idea for /media/disk to /media/disk_two just in case i try to use a flash drive too) except noone but root can do anything to it. I want everyone to be able to use it so they can put movies and stuff on it.

---

### Post by taurus on 2009-03-13
If you want everyone to have permission to write to /media/disk_two, then change the permissions with chmod.

```
sudo chmod -R 777 /media/disk_two
ls -la /media
```

---

### Post by bobmatino17 on 2009-03-13
this is the output from ls -al /media for disk_two
```
4 drwxrwxrwx 3 root root 4096 2009-03-13 12:16 disk_two
```

---

### Post by taurus on 2009-03-13
So can you write to /media/disk_two?

```
touch /media/disk_two/testing
ls -la /media/disk_two
```

---

### Post by bobmatino17 on 2009-03-16
```
total 24
drwxrwxrwx 3 root      root       4096 2009-03-16 19:59 .
drwxr-xr-x 4 root      root       4096 2009-03-16 19:55 ..
drwxrwxrwx 2 root      root      16384 2009-03-13 12:16 put_your_files_in_here
-rw-r--r-- 1 tuxiscool tuxiscool     0 2009-03-16 19:59 testing
tuxiscool@tuxiscool-desktop:~$ 

```

the "put_your_files_here" folder was lost+found, but i renamed it. it was odd because a could modify the folder and anything in it even though it appears to be owned by root.

---

### Post by taurus on 2009-03-16
But world has permissions to edit everything in /media/disk_two.  Isn't that what you want, world writable.

---

### Post by bobmatino17 on 2009-03-16
yes. i now notice that... ty.

---

