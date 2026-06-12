---
title: "problem mounting device"
date: 2009-01-20
forum: General Help
---

### Post by orduek on 2009-01-20
I had a nice good mythbuntu 8.10 system that worked and had a /var/lib as a xfs partition.
After messing around with it I tried to install Mythbuntu again, and left the xfs partition un touched.
But - I can't reach that partition anymore, I can see it in blkid command as /dev/sda6 but can't mount it.
How can I reach it in order to get my files from there?

---

### Post by taurus on 2009-01-20
How did you try to mount it and what was the error message?  Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by orduek on 2009-01-20
this is the output of those commands:
```
 sudo fdisk -l
[sudo] password for ormetal: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f3ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       60801   476664615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584       60801   475668553+  8e  Linux LVM
ormetal@HTPC:~$ sudo blkid
/dev/sda1: UUID="574adc8b-88db-4bce-a3f2-eaf9e3d2ec7d" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="37122b73-1841-dcaa-af93-b209424eee76" 
/dev/ramzswap0: TYPE="swap" 
ormetal@HTPC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=574adc8b-88db-4bce-a3f2-eaf9e3d2ec7d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=37122b73-1841-dcaa-af93-b209424eee76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ormetal@HTPC:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  1.9G  8.7G  18% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  372K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M     0 1012M   0% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
ormetal@HTPC:~$ 


```

---

### Post by taurus on 2009-01-20
> **orduek said:**
> this is the output of those commands:
```
 sudo fdisk -l
[sudo] password for ormetal: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f3ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       60801   476664615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
**[COLOR="Blue"]/dev/sda6            1584       60801   475668553+  8e  Linux LVM[/COLOR]**
ormetal@HTPC:~$ sudo blkid
/dev/sda1: UUID="574adc8b-88db-4bce-a3f2-eaf9e3d2ec7d" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="37122b73-1841-dcaa-af93-b209424eee76" 
/dev/ramzswap0: TYPE="swap" 
ormetal@HTPC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=574adc8b-88db-4bce-a3f2-eaf9e3d2ec7d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=37122b73-1841-dcaa-af93-b209424eee76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ormetal@HTPC:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  1.9G  8.7G  18% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  372K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M     0 1012M   0% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
ormetal@HTPC:~$ 


```

/dev/sda6 is LVM--logical volume manager.

What's the output of this command from a terminal?

```
ls -la /dev/mapper
```

---

### Post by orduek on 2009-01-20
```
ormetal@HTPC:~$ ls -la /dev/mapper
total 0
drwxr-xr-x  2 root root     60 2009-01-20 22:51 .
drwxr-xr-x 15 root root  14360 2009-01-20 22:51 ..
crw-rw----  1 root root 10, 60 2009-01-20 22:51 control
ormetal@HTPC:~$ 

```

---

### Post by taurus on 2009-01-20
Did you encrypt /dev/sda6?

[http://ubuntuforums.org/showthread.php?t=940904&highlight=mount+lvm+partition](http://ubuntuforums.org/showthread.php?t=940904&highlight=mount+lvm+partition)

---

### Post by orduek on 2009-01-20
No I didn't.
I just re-installed Mythbuntu and left that partition untouched.

---

### Post by taurus on 2009-01-20
Is there anything on /dev/sda6?  You can format it to ext3 if you wish.

---

### Post by orduek on 2009-01-20
Oh,
there's all my movies and recordings - it is important to try and save what's there.

---

### Post by taurus on 2009-01-20
Here's another one.

[http://ubuntuforums.org/showthread.php?t=664752](http://ubuntuforums.org/showthread.php?t=664752)

---

### Post by orduek on 2009-01-20
It's not working.
any other ideas?

---

### Post by taurus on 2009-01-20
How it's not working?  What have you done so far to try to mount it?

---

### Post by orduek on 2009-01-21
I installed lvm2.
modprobe the things that were written in the posts.
when trying to mount I write:
sudo mount /dev/sda6 /mnt/sda6 - it doesn't work or any other /mnt/* command.
I think maybe my mount command is not perfectly right?

I trying same things from live CD with same results.

When writing sudo vgscan I get nothing - maybe he doesn't find it?

---

### Post by orduek on 2009-01-21
OK, fixed it.
I used sudo xfs_repair /dev/sda6
after a long time he said something about finding secondary something. he asked me to try and mount it again - I did - It worked!
Thank you very much for your help.

---

