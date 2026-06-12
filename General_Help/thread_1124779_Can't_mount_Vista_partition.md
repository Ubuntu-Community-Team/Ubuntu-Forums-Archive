---
title: "Can't mount Vista partition"
date: 2009-04-13
forum: General Help
---

### Post by psychoadonis on 2009-04-13
I can't see the Vista partition in 'Places'

here's the result of fdisk:

This is what I get when I type fdisk:

psychoadonis@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 6 1280 10240000 7 HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 * 1280 38914 302289240 7 HPFS/NTFS
psychoadonis@ubuntu:~$

Any ideas?

---

### Post by taurus on 2009-04-13
Is your vista on /dev/sda3?

```
sudo mkdir /media/sda3
sudo mount -t ntfs-3g /dev/sda3 /media/sda3
df -h
```

---

### Post by psychoadonis on 2009-04-13
I tried pasting that code using sda3, sda2 and sda1, nothing mounts the vista partition. Here are the results:

**with sda3**

psychoadonis@ubuntu:~$ sudo mkdir /media/sda3
mkdir: cannot create directory `/media/sda3': File exists
psychoadonis@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda3 /media/sda3
psychoadonis@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.3G  3.3G  4.6G  42% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  108K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
/dev/sda3             289G  263G   26G  92% /host
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3             289G  263G   26G  92% /media/sda2
/dev/sda3             289G  263G   26G  92% /media/sda1
/dev/sda3             289G  263G   26G  92% /media/sda3
psychoadonis@ubuntu:~$ 


**sda2**

psychoadonis@ubuntu:~$ sudo mkdir /media/sda2
mkdir: cannot create directory `/media/sda2': File exists
psychoadonis@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/sda2
psychoadonis@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.3G  3.3G  4.6G  42% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  108K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
/dev/sda3             289G  263G   26G  92% /host
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3             9.8G  6.8G  3.1G  69% /media/sda2
/dev/sda3             289G  263G   26G  92% /media/sda1
/dev/sda3             289G  263G   26G  92% /media/sda3
/dev/sda2             9.8G  6.8G  3.1G  69% /media/sda2
psychoadonis@ubuntu:~$ 


**sda1**

psychoadonis@ubuntu:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
psychoadonis@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/sda1
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
psychoadonis@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      8.3G  3.3G  4.6G  42% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  112K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
/dev/sda3             289G  263G   26G  92% /host
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda3             9.8G  6.8G  3.1G  69% /media/sda2
/dev/sda3             289G  263G   26G  92% /media/sda1
/dev/sda3             289G  263G   26G  92% /media/sda3
/dev/sda2             9.8G  6.8G  3.1G  69% /media/sda2
psychoadonis@ubuntu:~$

---

### Post by taurus on 2009-04-13
> 
/dev/sda3 9.8G 6.8G 3.1G 69% /media/sda2
/dev/sda3 289G 263G 26G 92% /media/sda1
/dev/sda3 289G 263G 26G 92% /media/sda3
/dev/sda2 9.8G 6.8G 3.1G 69% /media/sda2

There they are.

```
ls -la /media/sda3
ls -la /media/sda2
```

p.s.  No need to mount the same partition, /dev/sda3, many times.

---

### Post by psychoadonis on 2009-04-13
I still don't understand, I pasted and here's what I got.
Still no partition

psychoadonis@ubuntu:~$ ls -la /media/sda3

total 4464105

drwxrwxrwx 1 root root       8192 2009-04-13 18:12 .

drwxr-xr-x 6 root root       4096 2009-04-13 21:30 ..

drwxrwxrwx 1 root root       4096 2008-02-04 21:23 Boot

-rwxrwxrwx 1 root root     333203 2008-01-20 21:50 bootmgr

-rwxrwxrwx 1 root root     546872 2008-06-24 20:22 bootmgr.efi

drwxrwxrwx 1 root root       8192 2009-04-13 13:37 Config.Msi

drwxrwxrwx 1 root root       8192 2009-02-06 01:44 DELL

-rwxrwxrwx 1 root root       3321 2008-12-08 04:12 dell.sdr

drwxrwxrwx 1 root root          0 2008-12-08 03:43 doctemp

drwxrwxrwx 1 root root          0 2009-01-11 19:57 Documents and Settings

drwxrwxrwx 1 root root          0 2009-04-13 12:08 DOS

drwxrwxrwx 1 root root          0 2008-09-03 04:44 Drivers

-rwxrwxrwx 1 root root        568 2009-04-05 12:23 INSTALL.LOG

drwxrwxrwx 1 root root          0 2008-12-08 02:38 Intel

-rwxrwxrwx 1 root root     904704 2006-12-02 00:37 msdia80.dll

drwxrwxrwx 1 root root          0 2009-01-15 11:29 MSOCache

-rwxrwxrwx 1 root root 4569112576 2009-04-13 13:37 pagefile.sys

drwxrwxrwx 1 root root          0 2008-01-20 22:04 PerfLogs

drwxrwxrwx 1 root root       8192 2009-04-08 23:14 ProgramData

drwxrwxrwx 1 root root       8192 2009-04-13 19:00 Program Files

drwxrwxrwx 1 root root      20480 2009-04-13 16:07 Program Files (x86)

drwxrwxrwx 1 root root       4096 2009-01-19 22:11 $Recycle.Bin

drwxrwxrwx 1 root root      20480 2009-04-13 16:07 System Volume Information

drwxrwxrwx 1 root root       4096 2009-01-15 11:49 temp

drwxrwxrwx 1 root root       4096 2009-03-23 11:50 ubuntu

drwxrwxrwx 1 root root       4096 2009-01-19 22:10 Users

drwxrwxrwx 1 root root      28672 2009-04-13 18:59 Windows

-rwxrwxrwx 1 root root     192307 2008-10-27 13:37 wubildr

-rwxrwxrwx 1 root root       8192 2008-10-27 13:37 wubildr.mbr

psychoadonis@ubuntu:~$ ls -la /media/sda2

total 52

drwxrwxrwx 1 root root  8192 2009-04-13 12:02 .

drwxr-xr-x 6 root root  4096 2009-04-13 21:30 ..

-rwxrwxrwx 1 root root 16448 2009-03-08 12:56 config.bin

drwxrwxrwx 1 root root     0 2008-12-08 05:18 dell

drwxrwxrwx 1 root root     0 2008-01-19 06:05 ProgramData

drwxrwxrwx 1 root root  4096 2009-02-16 23:44 Program Files

drwxrwxrwx 1 root root  4096 2009-02-23 21:56 $RECYCLE.BIN

drwxrwxrwx 1 root root     0 2008-01-29 12:56 sources

drwxrwxrwx 1 root root     0 2008-12-07 20:16 System Volume Information

drwxrwxrwx 1 root root     0 2009-04-13 18:42 Temp

drwxrwxrwx 1 root root  4096 2008-12-08 05:39 Tools

drwxrwxrwx 1 root root     0 2008-01-19 06:05 Users

drwxrwxrwx 1 root root  8192 2008-12-08 05:16 Windows

psychoadonis@ubuntu:~$

---

### Post by Polygon on 2009-04-13
this line caught my attention:

> 
Partition 2 does not end on cylinder boundary.


can you boot vista? maybe run a checkdisk on the vista partition you are trying to mount then try again?

---

### Post by psychoadonis on 2009-04-14
How do I do that?

---

### Post by tamas305 on 2009-04-14
I have had troubles with my Vista partition also. I have Ubuntu full install on a USB drive and whenever I boot off of it and try to access my computer OS (the c drive)drive I also get a cannot mount partition error. I have noticed that this always occurs with NTFS drives (all default windows configured drives) when Vista is not shutdown properly. Unfortunately the only way I have found to correct this problem is by logging back into Vista and shutting down correctly. 

Also, if you have any removable drives that are NTFS you have to make sure that you safely eject hardware or else Ubuntu will not be able to mount it correctly. I believe this is because Vista leaves unclean registries that it usually cleans up and it cause Ubuntu a world of problems.


-tamas

***********************************************
java + eclipse = happiness

---

### Post by psychoadonis on 2009-04-15
But I have ubuntu on my hard disk, and I always shut down properly

---

