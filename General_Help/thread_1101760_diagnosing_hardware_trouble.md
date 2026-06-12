---
title: "diagnosing hardware trouble"
date: 2009-03-20
forum: General Help
---

### Post by childofGod on 2009-03-20
I am having trouble on bootup.  I get error 18 when loading grub 1.5.  I have used the live cd to reload grub once and it worked but not subsequently.  When I use the live cd everything seems fully functional, except that I can see my hard disk exists but cannot access it.  I can surf the net, access my network, open files on an external hard drive but I cannot open any files on my hard disk (hd0).  The computer does not boot into the live disk properly consistently and for a while I could restart the computer repeatedly using hd0 and eventually get it to operate. That stopped working, too last week.  I am fairly certain I have a hardware problem but am not sure how to diagnose without removing the hard drive and installing in another machine.  Is there a way to do this using the live cd?  I know there is a memtest option on startup with the cd but I don't know how to understand the results.  Can anyone advise?

---

### Post by ushills on 2009-03-20
try running fdisk -l to find out which drives are connected then fsck /dev/sd whatever the drive listed to check the hard drive.

do this from a live cd.

---

### Post by childofGod on 2009-03-20
Thanks!  I'll definitely try that in the AM.  It's bedtime here on my side of the Pond.

---

### Post by childofGod on 2009-03-21
Here's what I get when running those commands. 

ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
ubuntu@ubuntu:~$ fsck /dev/sda
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Permission denied while trying to open /dev/sda
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo fsck /dev/sdb
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

Other than what I already knew, which is that I can't access my hard drive is this telling me whether my hard drive is damaged or not?

---

### Post by miegiel on 2009-03-21
At your disks manufacturers site you can download a "live CD" like image to test your disk.

ps
Start with backingup if there is anything important on the disk.

---

