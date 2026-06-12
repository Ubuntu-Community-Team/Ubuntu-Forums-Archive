---
title: "DVD multisession burning with gnomebaker"
date: 2006-01-05
forum: Desktop Environments
---

### Post by yccheok on 2006-01-05
By refering to [http://www.ubuntuforums.org/showthread.php?t=93020&highlight=gnomebaker+multisession](http://www.ubuntuforums.org/showthread.php?t=93020&highlight=gnomebaker+multisession),

I use the following steps to perform multisession burning:

1. yccheok@ubuntu:~$ ls -al /dev/ | grep dvd
lrwxrwxrwx 1 root root 3 2006-01-05 21:44 dvd -> hdc
lrwxrwxrwx 1 root root 3 2006-01-05 21:44 dvdrw -> hdc


2. sudo vi /etc/fstab

Add the following line at the end of the file.

/dev/hdc /media/cdrecorder udf,iso9660 ro,user,noauto 0 0

3.
sudo umount /dev/hdc

4. Gnomebaker->Actions->Import session



5. I get the following error:

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
cdrecord: Unspecified command not implemented for this drive.
cdrecord: Cannot read first writable address

Any suggestion? I am using gnomebaker 0.4.2

Thank you.

---

### Post by finite9 on 2006-08-17
Just want to say I get exact same error, but im using Gnomebaker 0.5.1 on Ubuntu 6.06 amd64 with a Matshita UJ-845D dual-layer 16x driver.  I have seen many threads just stating that they cannot burn DVDs.  I can burn CDs fine (uses cdrecord) but I heard that burning DVDs uses growisofs??  So dont know if this is a real cdrecord error.

Anyway, I get this error when trying to import a session from a DVD-RW using Gnomebaker.

---

### Post by ored on 2007-12-02
I've installed **[COLOR="Red"]brasero[/COLOR]** on ubuntu gutsy and it worked fine for me.
I hope it helps.

---

