---
title: "disk full - root directory has 8.7G !!"
date: 2009-04-18
forum: General Help
---

### Post by walter_j on 2009-04-18
My ubuntu partition is full. du -sh lists the root directory as having 8.7G. What could be in the root directory that takes up that much space? I looked through it but I didn't see anything obvious taking up gigs of space.

walter@walter-ubuntu:/$ sudo du -sh * 
6.1M	bin
54M	boot
0	cdrom
2.9M	dev
17M	etc
14G	home
4.0K	initrd
0	initrd.img
0	initrd.img.old
427M	lib
16K	lost+found
12K	media
12K	mnt
471M	opt
du: cannot access `proc/6479/task/6479/fd/3': No such file or directory
du: cannot access `proc/6479/task/6479/fdinfo/3': No such file or directory
du: cannot access `proc/6479/fd/3': No such file or directory
du: cannot access `proc/6479/fdinfo/3': No such file or directory
0	proc
8.7G	root
7.2M	sbin
32K	sqlurJsiI
200K	srv
0	sys
520K	tmp
3.4G	usr
454M	var


walter@walter-ubuntu:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             14535520  14267792         0 100% /
tmpfs                  1555968         0   1555968   0% /lib/init/rw
varrun                 1555968       336   1555632   1% /var/run
varlock                1555968         0   1555968   0% /var/lock
udev                   1555968      2884   1553084   1% /dev
tmpfs                  1555968        12   1555956   1% /dev/shm
lrm                    1555968      2000   1553968   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda10            93908420  13989860  75185816  16% /home
overflow                  1024       524       500  52% /tmp

I recently backed up the system using grsync to a second hd, and started having problems after that.

walter

---

### Post by danwood76 on 2009-04-18
Can you post the output of:
```

sudo ls -l /root

```
Do you use the root account, or use things like nautilus with root permissions?

---

### Post by walter_j on 2009-04-18
[QUOTE=danwood76;7095231]Can you post the output of:
```

sudo ls -l /root

```
Do you use the root account, or use things like nautilus with root permissions?[/QUOTE

walter@walter-ubuntu:/$ sudo ls -l /root
[sudo] password for walter: 
total 4
drwxr-xr-x 2 root root 4096 2009-04-16 18:44 Desktop

I don't log in as su. I occasionally use nautilus with root permissions, but it's rare, and not recently.

---

### Post by justin_guerin on 2009-04-18
> **walter_j said:**
> [QUOTE=danwood76;7095231]Can you post the output of:
```

sudo ls -l /root

```
Do you use the root account, or use things like nautilus with root permissions?[/QUOTE

walter@walter-ubuntu:/$ sudo ls -l /root
[sudo] password for walter: 
total 4
drwxr-xr-x 2 root root 4096 2009-04-16 18:44 Desktop

I don't log in as su. I occasionally use nautilus with root permissions, but it's rare, and not recently.
OK, now try these, and post the output:

ls -lA /root

du -sh /root/Desktop

As the output from du in your first post shows, you've got something large in /root.  Don't forget to check for hidden files (.*).

---

### Post by walter_j on 2009-04-18
walter@walter-ubuntu:/$ ls -lA /root
total 120
drwx------ 2 root root 4096 2008-12-19 21:58 .aptitude
-rw------- 1 root root  124 2009-04-17 19:58 .bash_history
-rw-r--r-- 1 root root 2227 2007-10-20 04:51 .bashrc
drwxr-xr-x 3 root root 4096 2008-11-01 09:44 .cache
drwx------ 4 root root 4096 2008-11-10 20:49 .config
drwx------ 3 root root 4096 2008-10-24 20:46 .dbus
drwxr-xr-x 2 root root 4096 2009-01-09 22:10 .debtags
drwxr-xr-x 2 root root 4096 2009-04-16 18:44 Desktop
-rw------- 1 root root   16 2008-11-01 03:37 .esd_auth
drwx------ 5 root root 4096 2009-04-17 20:55 .gconf
drwx------ 2 root root 4096 2009-04-17 22:31 .gconfd
drwx------ 4 root root 4096 2009-04-16 18:44 .gnome2
drwx------ 2 root root 4096 2008-07-16 08:28 .gnome2_private
drwx------ 2 root root 4096 2009-04-15 21:03 .grsync
drwxr----- 2 root root 4096 2009-02-14 19:00 .hplip
-rw------- 1 root root    0 2008-10-18 19:34 .ICEauthority
drwx------ 3 root root 4096 2008-09-18 07:03 .kde
drwxr-xr-x 3 root root 4096 2008-11-01 09:44 .local
drwxr-xr-x 3 root root 4096 2008-09-18 07:03 .mcop
-rw------- 1 root root   31 2008-10-16 08:11 .mcoprc
drwxr-xr-x 3 root root 4096 2009-04-16 18:44 .nautilus
-rw-r--r-- 1 root root  141 2007-10-20 04:51 .profile
drwxr-xr-x 2 root root 4096 2008-11-01 08:35 .pulse
-rw------- 1 root root  256 2008-11-01 08:35 .pulse-cookie
drwxr-xr-x 2 root root 4096 2008-09-18 07:03 .qt
-rw------- 1 root root 2563 2009-04-15 22:51 .recently-used.xbel
-rw------- 1 root root 1024 2008-10-19 09:27 .rnd
drwx------ 3 root root 4096 2009-04-17 18:20 .synaptic
drwx------ 3 root root 4096 2009-04-17 20:37 .thumbnails
drwxr-xr-x 2 root root 4096 2008-11-01 08:31 .wapi
drwxr-xr-x 2 root root 4096 2009-03-16 08:27 .xine


walter@walter-ubuntu:/$ du -sh /root/Desktop
4.0K	/root/Desktop
walter@walter-ubuntu:/$ 

it seems odd that the file sizes listed in du don't seem to add up to 15G. A quick estimate seems to show about 12 G. I ran fsck at startup, emptied trash, ran apt-get clean, cleared firefox history with no change.

---

### Post by justin_guerin on 2009-04-18
> **walter_j said:**
> walter@walter-ubuntu:/$ ls -lA /root
total 120
drwx------ 2 root root 4096 2008-12-19 21:58 .aptitude
-rw------- 1 root root  124 2009-04-17 19:58 .bash_history
-rw-r--r-- 1 root root 2227 2007-10-20 04:51 .bashrc
drwxr-xr-x 3 root root 4096 2008-11-01 09:44 .cache
drwx------ 4 root root 4096 2008-11-10 20:49 .config
drwx------ 3 root root 4096 2008-10-24 20:46 .dbus
drwxr-xr-x 2 root root 4096 2009-01-09 22:10 .debtags
drwxr-xr-x 2 root root 4096 2009-04-16 18:44 Desktop
-rw------- 1 root root   16 2008-11-01 03:37 .esd_auth
drwx------ 5 root root 4096 2009-04-17 20:55 .gconf
drwx------ 2 root root 4096 2009-04-17 22:31 .gconfd
drwx------ 4 root root 4096 2009-04-16 18:44 .gnome2
drwx------ 2 root root 4096 2008-07-16 08:28 .gnome2_private
drwx------ 2 root root 4096 2009-04-15 21:03 .grsync
drwxr----- 2 root root 4096 2009-02-14 19:00 .hplip
-rw------- 1 root root    0 2008-10-18 19:34 .ICEauthority
drwx------ 3 root root 4096 2008-09-18 07:03 .kde
drwxr-xr-x 3 root root 4096 2008-11-01 09:44 .local
drwxr-xr-x 3 root root 4096 2008-09-18 07:03 .mcop
-rw------- 1 root root   31 2008-10-16 08:11 .mcoprc
drwxr-xr-x 3 root root 4096 2009-04-16 18:44 .nautilus
-rw-r--r-- 1 root root  141 2007-10-20 04:51 .profile
drwxr-xr-x 2 root root 4096 2008-11-01 08:35 .pulse
-rw------- 1 root root  256 2008-11-01 08:35 .pulse-cookie
drwxr-xr-x 2 root root 4096 2008-09-18 07:03 .qt
-rw------- 1 root root 2563 2009-04-15 22:51 .recently-used.xbel
-rw------- 1 root root 1024 2008-10-19 09:27 .rnd
drwx------ 3 root root 4096 2009-04-17 18:20 .synaptic
drwx------ 3 root root 4096 2009-04-17 20:37 .thumbnails
drwxr-xr-x 2 root root 4096 2008-11-01 08:31 .wapi
drwxr-xr-x 2 root root 4096 2009-03-16 08:27 .xine


walter@walter-ubuntu:/$ du -sh /root/Desktop
4.0K	/root/Desktop
walter@walter-ubuntu:/$ 

it seems odd that the file sizes listed in du don't seem to add up to 15G. A quick estimate seems to show about 12 G. I ran fsck at startup, emptied trash, ran apt-get clean, cleared firefox history with no change.

My guess would be one of the hidden directories in /root/.  Run this command:

du -sh /root/.[^.]* | sort -bgr

The output will show the largest folder in /root/.  Depending on the results, check inside the largest folders, and hopefully you'll find out what's using that disk space.

---

### Post by walter_j on 2009-04-18
it appears there's 8.7 G in Trash. I already tried to empty the trash. Should I try to delete files out of the trash? I notice there's some of my backup in the trash. Maybe problems started when I ran out of space when trying to back up (forgot to mount the second disk, and started backup to /mnt/disk2 so backup went into the disk2 directory, not the 2nd hd). Ran out of space and deleted the backup in /mnt/disk2.

---

### Post by justin_guerin on 2009-04-18
> **walter_j said:**
> it appears there's 8.7 G in Trash. I already tried to empty the trash. Should I try to delete files out of the trash? I notice there's some of my backup in the trash. Maybe problems started when I ran out of space when trying to back up (forgot to mount the second disk, and started backup to /mnt/disk2 so backup went into the disk2 directory, not the 2nd hd). Ran out of space and deleted the backup in /mnt/disk2.

OK, all you need to do is delete the files from the trash.  But you'll have to do it with rm from the command prompt, or log in as root and just empty the trash.

---

### Post by walter_j on 2009-04-18
> **justin_guerin said:**
> OK, all you need to do is delete the files from the trash.  But you'll have to do it with rm from the command prompt, or log in as root and just empty the trash.

This solved the problem Thanks Justin!

How do I mark this as solved?

---

### Post by justin_guerin on 2009-04-18
> **walter_j said:**
> This solved the problem Thanks Justin!

How do I mark this as solved?

I'm not sure, since I've never done it.  From what I can gather, adding a solved tag seems to be the proper way.  It looks like you've already done so.

Glad I could help.

---

### Post by danwood76 on 2009-04-18
SOlved tags no longer exist, they were removed for some reason!

---

