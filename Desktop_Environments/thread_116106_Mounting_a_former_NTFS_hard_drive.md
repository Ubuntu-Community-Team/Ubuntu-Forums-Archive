---
title: "Mounting a former NTFS hard drive"
date: 2006-01-11
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-01-11
Ok.....

I had a 2nd 400GB hard-drive that was formatted as an NTFS before i started this little venture with this machine.  I realized upon first install that i couldn't see the drive at all.  I did some research and found that by mounting an NTFS drive that i would only have read access.  I didn't like that.

So i backed up my data to an external hard-drive my workplace had and wasn't using and plugged the drive back in.

Going to System --> Admin --> Disks it sees my 400GB /dev/hdb, but gives me no info for it, nor any options in which to do any thing.

I followed the directions found here:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)

and i get an error when i get to the mounting part (before editting fstab)

> 
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@ubuntu:~# mkdir /opt2
root@ubuntu:~# mount -t ext3 /dev/hdb1 /opt2
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so




I still can't view it in my file system at all.  So just curious as to how to alleviate this little last problem i'm having.  I have to start re-storing data to this drive tonight, as this external drive needs to be quietly returned tomorrow morning.

Again, any help is greatly appreciated :)

---

### Post by soulestream on 2006-01-12
> Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@ubuntu:~# mkdir /opt2

you should have 

mkfs -t ext3 /dev/hdb1

in between fdisk and mounting it.

right now it has no filesystem on it

soule

---

### Post by DigitalDuality on 2006-01-12
ok now i get this.....> root@ubuntu:~# mkfs -t ext3 /dev/hdb1
mke2fs 1.38 (30-Jun-2005)
/dev/hdb1: Invalid argument passed to ext2 library while setting up superblock


So did it write a file system? I'm guessing no.

---

### Post by soulestream on 2006-01-12
looks like you didnt make the partition

try 

cfdisk /dev/hdb

its a little more user freindly than fdisk

make the partitions and the select "write" then exit

then try to run mkfs


soule

---

### Post by DigitalDuality on 2006-01-12
Ok... looks good... kinda.

I mounted it to  /hdb  

i go to that folder, right click, properties.. and i see there's the correct amount of free space there.

But it's not listed Computer, or is it on the desktop as a drive.  It simply looks like another folder.

Though it is listed under Sys --> Admin --> Disks now.  

It shows it there, with a partition, formated as ext3 filesystem, device listed as /dev/hdb

but under status it states "Inaccessible".

What am i missing out on doing?

---

### Post by aysiu on 2006-01-12
You don't have to use the command-line. I'm pretty sure you can use GParted or QTParted if the drive is plugged in and not mounted.

---

### Post by DigitalDuality on 2006-01-12
I'll be sure to check out those apps, but it's probably best for me to get used to the command line.

---

### Post by DigitalDuality on 2006-01-12
still no luck with either cfdisk /dev/hdb or Gparted. :\

---

### Post by aysiu on 2006-01-12
[QUOTE=DigitalDuality]still no luck with either cfdisk /dev/hdb or Gparted. :\[/QUOTE] Last resort... try [this](http://www.ubuntuforums.org/showthread.php?t=114142)?

---

### Post by DigitalDuality on 2006-01-12
Would anyone mind looking the instructions on this link over and tell me if it's wrong in any way shape or form. B/c i've now done this 7 times.  Done the cfdisk twice, and Gparted once (following an attempt at mounting)... and still i have no drive.  I would like to start from scratch just to make sure i got it right and learn something.. right now though my mind is kinda running in circles and i'm getting stuff mixed up b/c i've been typing the same commands over and over and over again.  I'm also at a point... i'm not even sure the status of this drive is.

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAdditionalHardDrive.html)

---

### Post by DigitalDuality on 2006-01-12
[QUOTE=soulestream]you should have 

mkfs -t ext3 /dev/hdb1

in between fdisk and mounting it.

right now it has no filesystem on it

soule[/QUOTE]
Ok... i've started from scatch.  using fdisk i deleted the original partition..and recreated it.

Now.. i went to make the file system (both the link i'm working off and your response are giving me the exact same command to put in)  and each time i enter it i get :
[b]
/dev/hdb1: Invalid argument passed to ext2 library while setting up superblock
[/b]

---

