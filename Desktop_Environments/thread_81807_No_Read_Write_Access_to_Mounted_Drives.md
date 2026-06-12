---
title: "No Read Write Access to Mounted Drives"
date: 2005-10-25
forum: Desktop Environments
---

### Post by saultpastor on 2005-10-25
I've been using Ubuntu for the past week and I find Breezy very compatable with my system, I have a few squawks but I have wireless now!!  Great Distro.

My current hang up is the mounting of other partitions with read only access.  I have read the forums extensively and tried many things to fix it but no dice.

Current fstab:

/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/Win_C    vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       /media/Win_D    vfat    defaults        0       0
/dev/hda8       /media/PCLos    ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0

I'm trying to get Win_C to be writeable it is fat32 and writeable in PCLinuxOS

I have also tried:
/dev/hda2       /media/Win_C    vfat    iocharset=utf8,user,umask=000   0       0

I have seen both suggested, also it seems like I was able to mount it with a commandline at one time, but this is not a good option for a laptop. 

sudo chown [user] /media/Win_C  = operation not permitted or some such error.

I'm all for security but this is frustrating, it also seems to be a common problem, with various solutions. Any Ideas?

Thanks for your help!

---

### Post by RSX311 on 2005-10-25
does your user account have access to write to that drive? maybe use chmod to change user rights for that drive to allow your user account to read and write to it.  Im not sure what mode to use, Im kind of a noob myself, but learning :razz:

---

### Post by SilentCacophony on 2005-10-25
Hi. I seem to remember having a similar problem. I can't remember the exact remedy, but I think this was it.

[I]/dev/hda2 /media/Win_C vfat iocharset=utf8,umask=000 0 0
[/I] looks just like my entry, so it should work.

First, if it was already mounted before you tried to change permissions in /etc/fstab, then you should unmount it before remounting your *changed* fstab entries, like so:

[B]sudo umount -l /dev/Win_C
sudo mount -a
[/B]
I believe that worked fine for me.

If you were to try to change ownership or permissions of the mount point, you also have to unmount it first, or it'll spit an error like the one you had. On my setup, doing so only leads to ownership being changed to root:root and full permissions for all users after romounting with **sudo mount -a**, regardless of the mount point status.

**EDIT** - It may also help to log out and back in to gnome, if it's from *Places* in Gnome/Nautilus that you're having trouble.

---

### Post by saultpastor on 2005-10-25
> does your user account have access to write to that drive? maybe use chmod to change user rights for that drive to allow your user account to read and write to it

umask=000 should provide read, write, and execute permission, but it is not, I'm not sure why?

I don't think you can set permissions on a vfat format with chmod. If you can then maybe that is what I'm missing. Besides it is quite cumbersome if I have to set permissions everytime I boot.

Thanks for the reply

---

### Post by saultpastor on 2005-10-25
[QUOTE=SilentCacophony]Hi. I seem to remember having a similar problem. I can't remember the exact remedy, but I think this was it.

[I]/dev/hda2 /media/Win_C vfat iocharset=utf8,umask=000 0 0
[/I] looks just like my entry, so it should work.[/QUOTE]

That's what's so frustrating, for some umask=000 has worked end of problem for me no joy.  That's the way it booted, so I don't thin umount/mount is the issue.

> 
First, if it was already mounted before you tried to change permissions in /etc/fstab, then you should unmount it before remounting your *changed* fstab entries, like so:

[B]sudo umount -l /dev/Win_C
sudo mount -a
[/B]
I believe that worked fine for me.

If you were to try to change ownership or permissions of the mount point, you also have to unmount it first, or it'll spit an error like the one you had. On my setup, doing so only leads to ownership being changed to root:root and full permissions for all users after romounting with **sudo mount -a**, regardless of the mount point status.

**EDIT** - It may also help to log out and back in to gnome, if it's from *Places* in Gnome/Nautilus that you're having trouble.

**did this:**
craig@travelmate:~$ sudo umount -l /media/Win_C
craig@travelmate:~$ sudo chown craig /media/Win_C
craig@travelmate:~$ sudo chgrp craig /media/Win_C
craig@travelmate:~$ sudo chown craig /dev/hda2
craig@travelmate:~$ sudo chgrp craig /dev/hda2

**checked permissions:**
craig@travelmate:~$ ls -l /dev/hda2
brw-rw----  1 craig craig 3, 2 2005-10-25 05:06 /dev/hda2

craig@travelmate:/media$ ls -l
drwxr-xr-x  20 root  root  4096 2005-10-18 10:39 PCLos
drwxr-xr-x   2 craig craig 4096 2005-10-22 20:59 Win_C
drwxr-xr-x  11 root  root  4096 1969-12-31 19:00 Win_D

remounted checked permissions:

craig@travelmate:/media$ ls -l
total 44
lrwxrwxrwx   1 root root     6 2005-10-18 04:50 cdrom -> cdrom0
drwxr-xr-x   2 root root  4096 2005-10-18 04:50 cdrom0
drwxr-xr-x   2 root root  4096 2005-10-18 04:50 hda1
drwxr-xr-x   2 root root  4096 2005-10-18 04:50 hda2
drwxr-xr-x   2 root root  4096 2005-10-18 04:50 hda6
drwxr-xr-x   2 root root  4096 2005-10-18 04:50 hda8
drwxr-xr-x  20 root root  4096 2005-10-18 10:39 PCLos
drwxrwxrwx  18 root root 16384 1969-12-31 19:00 Win_C
drwxr-xr-x  11 root root  4096 1969-12-31 19:00 Win_D

Like I said frustrating!

This may indicate what the problem is but I have no desire to be changing ownership group or permission everytime I boot, fstab should take care of it.

Thanks please keep trying...

---

### Post by SilentCacophony on 2005-10-25
> craig@travelmate:~$ sudo chown craig /dev/hda2
craig@travelmate:~$ sudo chgrp craig /dev/hda2

Hmm. I don't think changing anything directly in /dev is necessary, or advisable. Never tried it, though. I don't know if that would be abstracted somehow, or if it would affect the filesystem. I'd think anything there should definately be root-owned, anyway, for the system to operate correctly. That's a bit over my head...

Anyway, my post above assumed that you hadn't rebooted since trying to change the fstab entries (guess I should have mentioned that.) A reboot should have taken care of the unmounting problem I described. I've had no problem other than when I initially changed mine, before I tried unmounting it first.

My only guess would be that you have possibly changed something inadvertantly that may be interfering.

I'll post some info on my setup, in case it helps at all:

```
*my /etc/fstab entry for a fat32 drive:*

brian@ubuntu:~$ cat /etc/fstab | grep hdb1
/dev/hdb1       /media/hdb1     vfat    iocharset=utf8,umask=000        0 0

*while unmounted, using **sudo umount /media/hdb1**:*

brian@ubuntu:~$ ls -l /dev | grep hdb1
brw-rw----  1 root disk      3,  65 2005-10-25 01:45 hdb1

brian@ubuntu:~$ ls -l /media | grep hdb1
drwxr-xr-x   2 root  root  4096 2005-10-14 13:36 hdb1

*while mounted as per /etc/fstab, using **sudo mount -a**:*

brian@ubuntu:~$ ls -l /dev | grep hdb1
brw-rw----  1 root disk      3,  65 2005-10-25 01:45 hdb1

brian@ubuntu:~$ ls -l /media | grep hdb1
drwxrwxrwx  14 root  root  8192 1969-12-31 19:00 hdb1
```

---

### Post by saultpastor on 2005-10-25
My result are very similar after a restart with the partitions mounted:

```
craig@travelmate:~$ ls -l /dev | grep hda2
brw-rw----  1 root disk      3,   2 2005-10-25 09:35 hda2
craig@travelmate:~$ ls -l /media | grep Win_C
drwxrwxrwx  18 root root 16384 1969-12-31 19:00 Win_C
```

I made a new user and logged into it to see if I had done something to change the rights of user craig.  Same problem as user craig.

I've seen this or similar problem in this forum several times and many of them either resolve with putting umask=000 in the fstab or they fizzle with someone having to work around it.  It doesn't seem like someting a person should have to live with. :confused:

---

### Post by SilentCacophony on 2005-10-25
[QUOTE=saultpastor]My result are very similar after a restart with the partitions mounted:

```
craig@travelmate:~$ ls -l /dev | grep hda2
brw-rw----  1 root disk      3,   2 2005-10-25 09:35 hda2
craig@travelmate:~$ ls -l /media | grep Win_C
drwxrwxrwx  18 root root 16384 1969-12-31 19:00 Win_C
```

I made a new user and logged into it to see if I had done something to change the rights of user craig.  Same problem as user craig.

I've seen this or similar problem in this forum several times and many of them either resolve with putting umask=000 in the fstab or they fizzle with someone having to work around it.  It doesn't seem like someting a person should have to live with. :confused:[/QUOTE]

If I gather correctly that you got the results in the code block above after a reboot, it shows full read/write/execute access for all users on /media/Win_C, so it should be writable.

As for adding umask=000 into fstab, that's just one common way people make FAT32 partitions writable. You may use other methods. Some people prefer to use *uid* and/or *gid* options for more security.

You can see a list of the options avaiable by entering **man mount** in a terminal and looking for the *-o* option section, and the *FILESYSTEM SPECIFIC MOUNT OPTIONS* section.

---

### Post by saultpastor on 2005-10-25
Thanks for all your help SilentCacophony, I just wanted to follow up on this.  It seems my problem is fixed.  I found one thread where someone stated the option needed to be umask=0000 the first zero indicates the type (or something?? I just don't remember the term) and the other 3 determine the permissions.

I remember seeing it with both 3 0's and 4 what is confusing is the tutorial:
[http://www.ubuntuguide.org/#automountfat]("http://www.ubuntuguide.org/#automountfat") which uses only 3.  I'm just glad to get it working.

A side note, I've used Linux for over 3 years, this is my first Debian, but This seems like something that would be expected by someone new to Linux, I realize it is a security risk, but whatever, my vote would be to ship it with these permissions set. but honestly what a great distro, I'm really impressed.

Thanks again

---

