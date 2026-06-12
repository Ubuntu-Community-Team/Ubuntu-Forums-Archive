---
title: "Copy read only files"
date: 2009-05-19
forum: General Help
---

### Post by apa240 on 2009-05-19
Well, I recently screwed up my Mac partition and I am now trying to get my files over to my Ubuntu install. Unfortunately my Mac partition is marked as read only and I can't change the permissions on it. I've used 'gksudo nautilus' and was able to access the files, but not copy them.

Is there anyway to copy the files over?

---

### Post by maheshasolkar on 2009-05-19
Generally, there should be no problem copying read-only files, as long as the destination of transfer is writable.

Can you list the files?

```
  ls -al mac_partition_mount_point
```

If you can list and navigate the directory structure on the Mac partition, you should be able to copy the files.

---

### Post by apa240 on 2009-05-19
> **maheshasolkar said:**
> Generally, there should be no problem copying read-only files, as long as the destination of transfer is writable.

That's what I thought, but it doesn't.


ls -al /media/Macintosh\ HD/
total 29264
drwxrwxr-t 1 root      80       35 2009-05-17 15:49 .
drwxr-xr-x 5 root root        4096 2009-05-19 19:58 ..
drwxrwxr-x 1 root      80       54 2009-05-12 23:45 Applications
drwxr-xr-x 1 root root          40 2009-05-12 23:02 bin
-rw-r--r-- 1 root root           0 2008-11-03 17:20 .com.apple.timemachine.supported
drwxrwxr-t 1 root      80        2 2007-09-23 17:37 cores
-rw-r--r-- 1 root      80    13312 2009-05-18 18:14 Desktop DB
-rw-r--r-- 1 root      80    17410 2009-05-17 15:48 Desktop DF
dr-xr-xr-x 1 root root           2 2007-09-23 17:37 dev
drwxrwxr-x 1 root      80        4 2008-11-04 17:45 Developer
-rw-r--r-- 1  501 dialout    15364 2009-05-18 18:55 .DS_Store
lrwxr-xr-x 1 root      80       11 2008-11-03 17:23 etc -> private/etc
drwx------ 1 root      80        5 2009-05-19 17:58 .fseventsd
dr-xr-xr-t 1 root root           2 2008-11-03 17:20 .HFS+ Private Directory Data?
dr-xr-xr-x 1 root      80        2 2008-11-03 17:46 home
-rw------- 1 root root      327680 2009-03-20 15:27 .hotfiles.btree
---------- 1 root root     8388608 2008-11-03 17:20 .journal
---------- 1 root root        4096 2008-11-03 17:20 .journal_info_block
drwxrwxr-t 1 root      80       52 2009-05-19 16:32 Library
-rw-r--r-- 1 root root    10361532 2009-04-01 01:55 mach_kernel
-rw-r--r-- 1 root root    10812566 2009-04-01 01:55 mach_kernel.ctfsys
dr-xr-xr-x 1 root      80        2 2008-11-03 17:46 net
drwxr-xr-x 1 root root           2 2007-09-23 17:37 Network
drwxr-xr-x 1 root root           6 2008-11-03 17:31 private
drwxr-xr-x 1 root root          66 2009-05-12 23:03 sbin
drwx------ 1 root      80        3 2009-03-06 13:10 .Spotlight-V100
drwxr-xr-x 1 root root           4 2009-05-12 23:37 System
lrwxr-xr-x 1 root      80       11 2008-11-03 17:23 tmp -> private/tmp
d-wx-wx-wt 1 root      99        2 2009-02-08 17:36 .Trashes
drwxr-xr-x 1 root      80        6 2009-03-28 20:02 Users
drwxr-xr-x 1 root root          11 2009-04-10 21:27 usr
lrwxr-xr-x 1 root      80       11 2008-11-03 17:23 var -> private/var
drwxr-xr-x 1 root root           2 2007-09-24 03:08 .vol
drwxrwxrwt 1 root      80        3 2009-05-19 17:58 Volumes

---

### Post by maheshasolkar on 2009-05-19
There are at least some directories that are not readable to you (or even root). Can you try copying just one file that is readable? For example:

```
  cp /media/Macintosh\ HD/dev/some_file ~/Desktop
```

---

### Post by michy99 on 2009-05-19
Is it possible that you are trying to copy them to a location that you do not have write permission for?

---

### Post by apa240 on 2009-05-19
I was able to copy music over. (I originally had changed these permissions on my Mac, so I could play them in Ubuntu.)

I guess my original post is slightly wrong then. I'm trying to get files from folders I have no access to. The owner of these folders (and full permissions) is '501', my Mac account.

---

### Post by maheshasolkar on 2009-05-19
> **apa240 said:**
> The owner of these folders (and full permissions) is '501', my Mac account.

Why not create a new user in Ubuntu with UID and GID 501? My be that will help. I have done that to setup NFS share with a Mac once.

```
  sudo addgroup macgrp 501
  sudo adduser --uid 501 your_mac_username
  sudo adduser your_mac_username macgrp
```

Then copy the files as the Mac user

```
  sudo -u your_mac_username /media/Macintosh\ HD/home/... ~/Desktop
```

Careful with the above commands, I've used them long back. Not tried them recently.

---

### Post by apa240 on 2009-05-19
I tried, but no luck. I got this as a response: 'sudo: no passwd entry for *name*!' (When I tried to copy the files.)

---

### Post by mike555 on 2009-05-19
You might try installing "nautilus-gksu" in Ubuntu from your package manager , then rt. click on the mac folder and use "open as administrator" ..... that has worked for me .

---

### Post by apa240 on 2009-05-19
> **mike555 said:**
> You might try installing "nautilus-gksu" in Ubuntu from your package manager , then rt. click on the mac folder and use "open as administrator" ..... that has worked for me .

That does the same thing as 'gksudo nautilus'.

---

### Post by maheshasolkar on 2009-05-19
While we are at it, here's one more thing to try. I am not sure it will work, but can you try booting off of a Live CD/USB disk? Then mount the disks/partitions in question and try to copy the files.

---

### Post by maheshasolkar on 2009-05-19
> **apa240 said:**
> I tried, but no luck. I got this as a response: 'sudo: no passwd entry for *name*!' (When I tried to copy the files.)

Did you reboot after creating the new user?

---

### Post by apa240 on 2009-05-20
> **maheshasolkar said:**
> While we are at it, here's one more thing to try. I am not sure it will work, but can you try booting off of a Live CD/USB disk? Then mount the disks/partitions in question and try to copy the files.


That worked, along with the use of 'gksudo nautilus' on the live cd. It gives root access to the copied files.

Thanks much for all your help.

---

