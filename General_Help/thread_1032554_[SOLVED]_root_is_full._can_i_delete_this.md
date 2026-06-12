---
title: "[SOLVED] root is full. can i delete this?"
date: 2009-01-06
forum: General Help
---

### Post by walter_j on 2009-01-06
My root partition is full. du returns:

walter@walter-ubuntu:/$ sudo du -sh * 
[sudo] password for walter: 
6.1M	bin
43M	boot
0	cdrom
3.7M	dev
16M	etc
du: cannot access `home/walter/.gvfs': Permission denied
50G	home
4.0K	initrd
0	initrd.img
0	initrd.img.old
337M	lib
16K	lost+found
36G	media
8.0K	mnt
384M	opt
du: cannot access `proc/7637/task/7637/fd/3': No such file or directory
du: cannot access `proc/7637/task/7637/fdinfo/3': No such file or directory
du: cannot access `proc/7637/fd/3': No such file or directory
du: cannot access `proc/7637/fdinfo/3': No such file or directory
0	proc
12M	root
7.4M	sbin
4.0K	srv
0	sys
40K	tmp
2.5G	usr
484M	var
0	vmlinuz
0	vmlinuz.old

/home is on a seperate partition and have lots of space there. I notice  /media has 36 G. I checked in media, and /media/disk-1 has 36 G. Does /media/disk-1 point to another partition (maybe xp)? Or does it actually have 36 GB in the root partition. What can I do to clean up some space. I enptied the trash and ran apt-get clean already.

other than /media it seems that all other directories in the root are relatively small. I think i gave the root partition 15 GB when i set up ubuntu. i'm surprised ubuntu still runs when the root is full.

walter

---

### Post by isparkes on 2009-01-06
you can also use

```
df -k
```

which will list all devices and the usage of the device. This is usually more useful for understanding what is full.

---

### Post by mcduck on 2009-01-06
/media/disk-1 is some other partition, most likely the windows partition you mentioned. (/media is where removable drives, CD's and such stuff gets mounted)

I don't really see anything special on that output. What does "df -h" say?

---

### Post by walter_j on 2009-01-07
> **mcduck said:**
> /media/disk-1 is some other partition, most likely the windows partition you mentioned. (/media is where removable drives, CD's and such stuff gets mounted)

I don't really see anything special on that output. What does "df -h" say?

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              40G   40G     0 100% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  356K 1003M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.9M 1001M   1% /dev
tmpfs                1004M  872K 1003M   1% /dev/shm
lrm                  1004M  2.0M 1002M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb3             120G   50G   64G  44% /home
overflow              1.0M   32K  992K   4% /tmp

---

### Post by chrisccoulson on 2009-01-07
> **walter_j said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              40G   40G     0 100% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  356K 1003M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.9M 1001M   1% /dev
tmpfs                1004M  872K 1003M   1% /dev/shm
lrm                  1004M  2.0M 1002M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb3             120G   50G   64G  44% /home
overflow              1.0M   32K  992K   4% /tmp

It seems that the space occupied by the files under /media are actually taking up space on your root filesystem, and not on a seprately mounted filesystem. You don't have any additional filesystems mounted under /media

---

### Post by walter_j on 2009-01-07
> **chrisccoulson said:**
> It seems that the space occupied by the files under /media are actually taking up space on your root filesystem, and not on a seprately mounted filesystem. You don't have any additional filesystems mounted under /media

I'm sure the file in /media/disk-1 is a backup i made with Simple Backup program. I thought I was backing up to a removeable hd. perhaps it created a temp backup first. I tried to delete it but I can't. 

sudo ls /media/disk-1
[sudo] password for walter: 
2008-12-17_16.36.16.157931.walter-ubuntu.ful
walter@walter-ubuntu:~$ sudo rm /media/disk-1/*.ful
rm: cannot remove `/media/disk-1/*.ful': No such file or directory

I tried gksudo nautilus, but I get a error message and nautilus won't start - prob because the disk is full. Waht can I do?

I started a root terminal and was able to check the directory. It was a backup. I deleted it and all is fine now. Thanks all

---

