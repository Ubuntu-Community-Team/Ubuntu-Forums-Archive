---
title: "unable to mount"
date: 2009-03-19
forum: General Help
---

### Post by sir.johneleth on 2009-03-19
Hello all. 

Having recently installed ubuntu on my laptop and loving it i had finaly got it set up the way i wanted.

I have 3 partions 
partition 1 - xp sp3  (my xp partion)
partition 2 - media   (my music)
partition 3 - linux    (Ubuntu partion)

Until recently I could mount the XP and media partition in ubuntu and today I find that I cant mount my media. 

Whenever I click on it get an error saying 
"Cannot mount volume
Invalid mount point option when attempting to mount the volume 'media'"

Am quite new to ubuntu so have hit a dead end in what to do. I have tried running a repair on the drive in xp and then restarting and going into ubuntu as this has solved any probolem i have had before. 

please help.
John

I can easily provide any information.

---

### Post by taurus on 2009-03-19
You did shut down windows cleanly the last time you used it, right?

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by sir.johneleth on 2009-03-19
yeah i did, only made that mistake once - maybe twice.

fdisk  -1
> user@ubuntu:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       12111    35841015    7  HPFS/NTFS
/dev/sda3           12112       14593    19936665    5  Extended
/dev/sda5           12112       14593    19936633+   7  HPFS/NTFS
user@ubuntu:~$ 


cat /etc/fstab
> user@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
user@ubuntu:~$ 


df -h
> user@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.3G  4.6G  3.3G  59% /
tmpfs                 370M     0  370M   0% /lib/init/rw
varrun                370M  124K  370M   1% /var/run
varlock               370M     0  370M   0% /var/lock
udev                  370M  2.7M  368M   1% /dev
tmpfs                 370M   12K  370M   1% /dev/shm
/dev/sda5              20G   11G  9.0G  54% /host
lrm                   370M  2.0M  368M   1% /lib/modules/2.6.27-11-generic/volatile
user@ubuntu:~$

---

### Post by sir.johneleth on 2009-03-20
solved using the site bellow

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/]("http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/")

---

