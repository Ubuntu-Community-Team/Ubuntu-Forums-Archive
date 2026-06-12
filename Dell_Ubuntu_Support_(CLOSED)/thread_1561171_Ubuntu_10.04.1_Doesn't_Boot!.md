---
title: "Ubuntu 10.04.1 Doesn't Boot!"
date: 2010-08-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pcscripts on 2010-08-25
I installed some updates on my Dell Dimension B110 computer running Ubuntu 10.04.1 and it told me I had to restart my computer. When my computer starts up, I always turn on verbose mode (press up arrow) to make sure it doesn't encounter any errors. Well it went through fsck and it said my filesystem was clean and then it just sat there doing nothing. It did the same time in recovery mode. Does anyone know how to fix this issue?

---

### Post by LieveWalrus on 2010-08-30
I have exactly the same problem but not on a dell. I think this isn't really dell related.
It's and old PC I tranformed into a home NAS, so installed ubuntu server 10.04 on a P4 with 1 GB ram. The fsck is being done on /dev/sda1 which is my root partition but the outcome of the fsck is that the filesystem is clean.

I tried working around the issue by booting up with a live cd and disabling the file system check in /etc/fstab... no luck, now it is just stuck I assume at the same point, but it just skipped the file system check...

---

### Post by pcscripts on 2010-08-31
I have narrowed down the problem to a package. I am trying to figure out which one it is but finding one package out of 2000 is like trying to find a needle in a haystack!
:confused:

---

### Post by forgewire on 2010-09-22
I couldn't even boot this thing on sony vaio from live CD

---

### Post by pcscripts on 2010-09-22
Well, my computer is fully up and running. I reinstalled, copied over my data from backups, and install only the packages I actually used. You should probably do the same.

---

