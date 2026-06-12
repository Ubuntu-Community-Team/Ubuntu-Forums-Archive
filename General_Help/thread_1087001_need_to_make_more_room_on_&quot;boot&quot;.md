---
title: "need to make more room on &quot;/boot&quot;"
date: 2009-03-04
forum: General Help
---

### Post by concerto on 2009-03-04
* can someone walk me through this? 

I can't upgrade to a newer version on Ubuntu unless I increase the boot partition.

My computer came pre-installed with Ubuntu.



When I try to upgrade I get this error...

Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 113M free space on disk '/boot'. Please free at least an additional 75.5M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.



Thank you so much.

---

### Post by lykwydchykyn on 2009-03-04
Can you post the output of "df -h" ?  Trash and package cache wouldn't affect the contents of /boot.  Also, the output of "ls -alh /boot" would be helpful.

---

### Post by concerto on 2009-03-04
concerto@concerto:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             290G   28G  248G  10% /
varrun                1.5G   96K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
/dev/sda3             193M  148M   36M  81% /boot
tmpfs                 1.5G   39M  1.5G   3% /lib/modules/2.6.24-23-generic/volatile
concerto@concerto:~$ ls -alh /boot
total 143M
drwxr-xr-x  4 root root 3.0K 2009-02-10 14:30 .
drwxr-xr-x 21 root root 1.0K 2009-03-04 10:28 ..
-rw-r--r--  1 root root 405K 2007-09-23 16:28 abi-2.6.20-16-generic
-rw-r--r--  1 root root 415K 2008-02-12 05:39 abi-2.6.22-14-generic
-rw-r--r--  1 root root 413K 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root 413K 2008-05-28 22:39 abi-2.6.24-18-generic
-rw-r--r--  1 root root 413K 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root 413K 2008-10-21 23:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root 413K 2008-11-24 17:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root 413K 2009-01-25 23:30 abi-2.6.24-23-generic
-rw-r--r--  1 root root  82K 2007-09-23 13:47 config-2.6.20-16-generic
-rw-r--r--  1 root root  74K 2008-02-12 05:39 config-2.6.22-14-generic
-rw-r--r--  1 root root  79K 2008-04-10 12:51 config-2.6.24-16-generic
-rw-r--r--  1 root root  79K 2008-05-28 22:39 config-2.6.24-18-generic
-rw-r--r--  1 root root  79K 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r--  1 root root  79K 2008-10-21 23:12 config-2.6.24-21-generic
-rw-r--r--  1 root root  79K 2008-11-24 17:47 config-2.6.24-22-generic
-rw-r--r--  1 root root  79K 2009-01-25 23:30 config-2.6.24-23-generic
drwxr-xr-x  2 root root 1.0K 2009-01-29 07:50 grub
-rw-r--r--  1 root root 6.6M 2007-11-29 13:19 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 6.6M 2007-11-29 12:32 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 7.3M 2008-06-03 18:06 initrd.img-2.6.22-14-generic
-rw-r--r--  1 root root 7.0M 2008-02-28 14:14 initrd.img-2.6.22-14-generic.bak
-rw-r--r--  1 root root 7.5M 2008-05-15 14:29 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7.5M 2008-05-15 14:27 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7.6M 2008-06-10 12:57 initrd.img-2.6.24-18-generic
-rw-r--r--  1 root root 7.5M 2008-06-04 10:17 initrd.img-2.6.24-18-generic.bak
-rw-r--r--  1 root root 7.6M 2008-08-26 11:09 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7.6M 2008-08-15 00:42 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7.6M 2008-11-09 14:52 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7.6M 2008-10-28 07:48 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7.6M 2009-01-07 11:54 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7.6M 2008-12-08 18:25 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7.6M 2009-02-10 14:30 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7.6M 2009-01-29 07:49 initrd.img-2.6.24-23-generic.bak
drwx------  2 root root  12K 2007-11-26 19:44 lost+found
-rw-r--r--  1 root root 101K 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root 789K 2007-09-23 16:30 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 805K 2008-02-12 05:39 System.map-2.6.22-14-generic
-rw-r--r--  1 root root 879K 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root 884K 2008-05-28 22:39 System.map-2.6.24-18-generic
-rw-r--r--  1 root root 884K 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 885K 2008-10-21 23:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 885K 2008-11-24 17:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root 885K 2009-01-25 23:30 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1.7M 2007-09-23 16:28 vmlinuz-2.6.20-16-generic
-rw-r--r--  1 root root 1.7M 2008-02-12 05:39 vmlinuz-2.6.22-14-generic
-rw-r--r--  1 root root 1.9M 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1.9M 2008-05-28 22:39 vmlinuz-2.6.24-18-generic
-rw-r--r--  1 root root 1.9M 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1.9M 2008-10-21 23:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1.9M 2008-11-24 17:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1.9M 2009-01-25 23:30 vmlinuz-2.6.24-23-generic
concerto@concerto:~$

---

### Post by concerto on 2009-03-04
So do I need to just empty out a folder or something?

---

### Post by Slim Odds on 2009-03-04
> **concerto said:**
> So do I need to just empty out a folder or something?

Remove a bunch of those old kernels......

You can also free some space by lowering the reserved space on that partition.

Use tune2fs with the -m option

---

### Post by lykwydchykyn on 2009-03-04
What you need to do is uninstall some of those old kernels.  You've got 8 kernels installed right now, which is 7 more than you need.

First, determine which kernel you're currently using with this command:
```

uname -r

```
Probably you're using the newest one, but it never hurts to check.

Then fire up synaptic and search for "linux-image".  Uninstall all the old versions of the kernel.  Make sure you DON'T uninstall your currently running one.  That'd be bad.

If you're worried, just uninstall 4 or 5 of them, starting with the oldest.  That should clean up enough room.

---

### Post by concerto on 2009-03-04
concerto@concerto:~$ uname -r
2.6.24-23-generic
concerto@concerto:~$ 


ok.  I am going to try to do this.  I will let you know how it goes.

---

### Post by concerto on 2009-03-04
Hey, It worked!  I now have a current version of Ubuntu!!!

Thank you. Thank you. Thank you.

---

