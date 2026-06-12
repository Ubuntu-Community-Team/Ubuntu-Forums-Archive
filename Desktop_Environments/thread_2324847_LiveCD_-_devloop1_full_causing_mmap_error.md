---
title: "LiveCD - /dev/loop1 full causing mmap error"
date: 2016-05-16
forum: Desktop Environments
---

### Post by wherbjr35 on 2016-05-16
Good evening all,

I am working with an Ubuntu LiveCD via 16GB flash drive to ultimately fix a WD mycloud 3TB hard drive.  Upon installing v.14.04, updating all packages, and then proceeding to install the progs necessary to fix the drive, i am now confronted with this error, when running ```
sudo apt-get install mdadm
``` from terminal, i get this error: 

```
Reading package lists... Error!
E: Unable to synchronize mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```

Googling let me to understand this is a space issue, however, i have plenty of room on the flash drive.  When running ```
df -h
```, i find that /dev/loop1 full. Not sure why it is sized so small..

```
Here is the output.
ubuntu@ubuntu:~$ df -h
Filesystem Size Used Avail Use% Mounted on
udev 3.9G 12K 3.9G 1% /dev
tmpfs 790M 1.5M 788M 1% /run
/dev/sdb1 16G 3.1G 13G 21% /cdrom
/dev/loop1 989M 989M 0 100% /rofs
/cow 2.0G 1.3G 640M 67% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
tmpfs 3.9G 1.1M 3.9G 1% /tmp
none 5.0M 0 5.0M 0% /run/lock
none 3.9G 80K 3.9G 1% /run/shm
none 100M 40K 100M 1% /run/user
/dev/md127 1.9G 729M 1.1G 41% /media/ubuntu/dea09609-1dfc-4e3f-bc27-08e8988ceaae
/dev/sda1 150G 137G 13G 92% /media/ubuntu/BA3C89A83C89606D
/dev/loop0 2.0G 1.3G 640M 67% /media/ubuntu/c5213a83-af28-ff4a-8ea0-4bc54e0621ed
/dev/sdd1 7.6G 7.2G 379M 96% /mnt/usb2
```

/dev/sdb1 refers to the primary partition of the flash drive i am using for the LiveCD. It has plenty of space. Would I need to resize /dev/sdb1 first to allocate free space, then resize /dev/loop1 to take in what was allocated? Is there something else i should do instead?

Thanks,
Wherbjr35

---

