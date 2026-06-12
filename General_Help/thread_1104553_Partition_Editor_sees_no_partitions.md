---
title: "Partition Editor sees no partitions"
date: 2009-03-23
forum: General Help
---

### Post by John GT on 2009-03-23
I have a drive that is NTFS formated, but the Partition Editor in Xubuntu sees the entire drive as unpartitioned and I get an error when trying to mount /dev/sda and /dev/sda1. Is there hope of data recovery? What can I try? (I'm using the LiveCD to recover some data, not trying to install)

---

### Post by drs305 on 2009-03-23
The partition table may be corrupted. An app called testdisk can do wonders in recovering from such problems. I am not an expert at using it but a regular poster named caljohnsmith is. You could search for some of his threads, but be specific because there are a lot of them out there. Including an exact error message might help the search.

---

### Post by lisati on 2009-03-23
I had a similar issue a while back after an install went haywire. If I recall correctly, it had something to do with the MBR and partitioning info being corrupted. Part of the solution on my machine was to boot into Windows in recovery mode and attempt repairs from there. (Since I'm not a hardware guru I might have to pass the reins on to someone else.)

---

### Post by meierfra. on 2009-03-23
Post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by John GT on 2009-03-23
Here is some more information:

Durring booting from the CD errors such as the following appear repeatedly:

Buffer I/O error on device sda1, logical block 16

exeption Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
(BMDMA stat 0x25)
cmd c8/00:08:bf:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in

The laptop is a Dell Latitude D600

Below is the output:
---------------------------------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b083b08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78124094    39062016    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 78124032, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
---------------------------------

I cannot boot into Windows, it gives the error:
A disk read error occurred
Press CTRL+ALT+DEL to restart

---

### Post by Slim Odds on 2009-03-23
You need to install ntfs-3g

By default, the LiveCD's don't do NTFS

---

### Post by John GT on 2009-03-23
Just for reference, Im using a CD of Xubuntu 7.10. I tried to boot from a previously working copy of Ubuntu 8.04, but it would hang when it had half loaded the desktop.

I loaded up the same disk on my Lenovo laptop and the Partition Editor was able to properly detect the NTFS partition there, so it is not a problem of missing any software packages. (Though it might be if I had actually tried to read any data.) At this point, I just want Xubuntu to recognize that the drive is formated.

---

### Post by meierfra. on 2009-03-23
There does not seem to be  a problem with your partition table. 

I suggest to run a file system check. Boot from an XP or Vista CD. Go to the repair console and type

```
chkdsk /r
```

You can also see whether testdisk can read your partition. Boot from the Xubuntu CD,  download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```

After starting testdisk with the above command, choose 
 "Proceed"
"Intel",
 "Analyze",
 "Quick search",
Press "Y" 
Select your ntfs partition (although it should be selected already)
Press  "p" to get a directory listing.
Press "esc" to get back to the previous menu.
Press Enter.

If pressing "p" gave you a listing of the files on your "NTFS" partition,  choose "write".

If not choose "Deep Search" and continue as after the "Quick Search"

---

### Post by John GT on 2009-03-23
I've been reading about TestDisk and it looks like it might be able to help, and I also want to try the different DOS/Windows tools that are on Windows disks in the recovery console. Unfortunatly, I dont have a power supply for this particular laptop, so I'm having to wait on one now that I've lost the inital charge in the laptop. (I'm working on it for a friend-of-a-friend) All that to say, be patient, it will be a while before I have any new information. Thanks.

---

