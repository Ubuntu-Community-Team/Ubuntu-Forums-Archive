---
title: "Access NTFS partition from GUI - How?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by xp_newbie on 2006-06-30
The NTFS partition is already mounted:

dr-x------ 1 root root 8192 2006-06-29 23:00 /tmp/disks-conf-sda1

But as can be seen above, only accessible to root.

I would like to be able to access it as a non-root user, by supplying the root password on demand (i.e. when I click on some directory, via desktop, I get prompted for a password by way of gksudo or similar).

I prefer not to permanently change permissions to that mount point (because then it will be readable by all users on the computer).

What is the proper way to do what I am trying to accomplish?

Thanks!
Alex

---

### Post by ericesque on 2006-06-30
there are nautilus scripts available that allow you to right click a folder or file and access it as su after entering a password.  It is very much like gksudo.

The easiest way I know of getting it is by using automatix.  (check the third party projects section of the forum to learn more)  You'll be able to install automatix and select to install nautilus scripts (or something like that).

---

### Post by xp_newbie on 2006-06-30
OK, I found a way. I don't know whether this is the best way, but it seems to work. 

1. Right-click toolbar > Add to Panel > Custom Application Launcher
2. Command:  gksudo nautilus /tmp/disks-conf-sda1

---

### Post by victor_c26 on 2006-07-03
I can read the files just fine, and open them. But this command doesn't let me copy those files. Anybody know of a way to let me copy the files over?

---

### Post by Thund3rstruck on 2006-07-03
on my machine I can see /etc/fstab mounts it as this:
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)

and my regular user account has the drive readable from the desktop

---

