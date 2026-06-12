---
title: "Mounting Issues"
date: 2009-01-31
forum: General Help
---

### Post by mistaWAC on 2009-01-31
So I'm using Ubuntu again after about a year hiatus and I've got a different setup than I used to.  Before I had the O/S installed on a 40gb HDD and storage on a 500gb HDD.  Now everything is on the 500gb in separate partitions.

My issue now is that I want to put the storage space in /media/storage and I can't figure out how to mount it there.  Any help?

---

### Post by taurus on 2009-01-31
What filesystem is that 40GB harddrive?  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by mistaWAC on 2009-01-31
The 40gb is no longer in there, just the 500gb now.

fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf770f86f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2675     1951897+  82  Linux swap / Solaris
/dev/sda3            2676       60801   466897095   83  Linux
```

blkid
```
/dev/sda1: UUID="317dabc8-605b-4e4f-af76-60d3023b5c9c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="8e22f93b-9af0-4c78-a5d0-7639c4316dd7" 
/dev/sda3: UUID="49e51c21-527d-45ed-9f51-850b5b60df93" SEC_TYPE="ext2" TYPE="ext3" 
```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=317dabc8-605b-4e4f-af76-60d3023b5c9c /               ext3    relatime,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sda2
UUID=8e22f93b-9af0-4c78-a5d0-7639c4316dd7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  3.4G   15G  20% /
varrun                506M  116K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   44K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-23-generic/volatile
```

---

### Post by taurus on 2009-01-31
I assume we are talking about the /dev/sda3.

Edit /etc/fstab
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=49e51c21-527d-45ed-9f51-850b5b60df93   /media/storage   ext3   defaults   0   2
```
Save it and exit gedit.  Then, mount it.

```
sudo mount -a
df -h
```

Now, if you want to write to /media/storage without using sudo/gksudo, you can change the ownership of /media/storage from root to your login name, assuming it's mista.

```
sudo chown -R mista:mista /media/storage
ls -la /media
```

---

### Post by mistaWAC on 2009-01-31
So with those directions I can set it to the FTP Folder too, right?  My FTP server needs to have the ability to allow other users to read and write as well...

---

### Post by taurus on 2009-01-31
It depends on which ftp server you are running on your machine.  You can allow others to upload to /home/ftp by configuring it.  Also, you probably need to change the permissions to that directory so others can write to it.

```
sudo chmod -R 777 /home/ftp
```

---

