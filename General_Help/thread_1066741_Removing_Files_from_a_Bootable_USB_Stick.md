---
title: "Removing Files from a Bootable USB Stick"
date: 2009-02-11
forum: General Help
---

### Post by 5BallJuggler on 2009-02-11
I have a partitioned 8Gb USB memory stick, I'm trying to remove the files on the 1st partition, but the system won't allow it. here is the output from the commands I would normally use

```
phil@phil-netbook:~$ sudo chown phil:phil /media/JetFlash220
chown: changing ownership of `/media/JetFlash220': Read-only file system

phil@phil-netbook:~$ sudo rm -rf /media/JetFlash220/PdtStart.exe
rm: cannot remove `/media/JetFlash220/PdtStart.exe': Read-only file system

phil@phil-netbook:~$ sudo chmod -R 666 /media/JetFlash220
chmod: changing permissions of `/media/JetFlash220': Read-only file system
chmod: changing permissions of `/media/JetFlash220/Autorun.inf': Read-only file system
chmod: changing permissions of `/media/JetFlash220/PdtData': Read-only file system
chmod: changing permissions of `/media/JetFlash220/PdtData/PdtPack.pak': Read-only file system
chmod: changing permissions of `/media/JetFlash220/PdtData/PdtReg.exe': Read-only file system
chmod: changing permissions of `/media/JetFlash220/PdtStart.exe': Read-only file system
```

The stick says it is a joliet CD, and is formatted to CDFS file type, is there a way to get the files off?

---

### Post by x33a on 2009-02-11
i have read a lot of similar thread of flash drives being read only, and mainly the cause was improper removal of the drive.

so if you were using it on a windows system and forgot to safely remove it, then you'll first have to safely remove it from a windows system.

try plugging it into a win pc and the try the safe removal.

---

### Post by 5BallJuggler on 2009-02-11
Thanks for your reply,

I have done this already, no difference in results.

---

### Post by x33a on 2009-02-11
what does fdisk -l say?

---

### Post by 5BallJuggler on 2009-02-11
```
phil@phil-netbook:~$ df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            150894048   4341952 138887088   4% /
tmpfs                   510856         0    510856   0% /lib/init/rw
varrun                  510856       108    510748   1% /var/run
varlock                 510856         0    510856   0% /var/lock
udev                    510856      2788    508068   1% /dev
tmpfs                   510856       104    510752   1% /dev/shm
lrm                     510856      2000    508856   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1              7771892     17340   7359760   1% /media/disk-1
/dev/scd0                38400     38400         0 100% /media/JetFlash220

phil@phil-netbook:~$ fdisk -l

Cannot open /dev/sda
Cannot open /dev/sdb

```

---

### Post by 5BallJuggler on 2009-02-11
fdisk /dev/scd0 gives me this:

```
phil@phil-netbook:~$ sudo fdisk /dev/scd0

[sudo] password for phil: 

You will not be able to write the partition table.
Note: sector size is 2048 (not 512)
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xc08bbe2b.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```

---

### Post by x33a on 2009-02-11
i guess the partition table is messed up. so you'll have to reformat the drive.

copy any important data and reformat it using gparted.

---

### Post by 5BallJuggler on 2009-02-11
GParted does not see the offending partition.

---

### Post by x33a on 2009-02-11
download the latest version of gparted. some people have problems with the older version.

or format it in windows.

---

### Post by 5BallJuggler on 2009-02-11
It already is the latest version (I think) 0.3.8-lubuntu2

```
phil@phil-netbook:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

dosfdsk gives me this:

```
phil@phil-netbook:~$  sudo dosfsck  -ar /dev/scd0

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/scd0:Read-only file system
```
 

Also Windows does not see it either.

---

### Post by x33a on 2009-02-11
latest version is GParted 0.4.2. but, it's not in the official repos. try installing it and see if it works.

---

### Post by tonymcm on 2009-09-28
I'm not sure if this thread is closed or if you still have this memory stick - I can reopen it if you want as I have been playing with my transcend 210 flash with the fingerprint reader and have figured out how to delete the files. I am working on installing my own tools to the (virtual) cd drive that appears when inserted.

Reply if you (or anyone) is still intrested in these devices

---

