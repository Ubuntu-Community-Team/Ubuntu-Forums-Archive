---
title: "Firefox out of order"
date: 2009-03-14
forum: General Help
---

### Post by geltonas on 2009-03-14
Hi, sorry if I put the thread not in the right category, and also I 've looked into firefox website I couldn't find to report a 'bug'.
So the problem is: 
when I launch the firefox it doesn't load home page, 
doesn't keep history of the last visited websites
even I can't go back and forward one page,
when I enter URL it doesn't prompt to me last visited websites.
how can I fix it or reinstall firefox

Any advise is welcome to hear
thank you

---

### Post by Insane_Homer on 2009-03-14
1st check that you've not run out of disk space on the volume

use terminal to run

```
df -h
```

check the % used columns

to re-install use package manager and select the re-install option

---

### Post by geltonas on 2009-03-14
It seems I ve run out of memory
      total       used       free     shared    buffers     cached
Mem:       2071392    1971756      99636          0     697968     722392
-/+ buffers/cache:     551396    1519996
Swap:      6064496          0    6064496
Total:     8135888    1971756    6164132

But I can't uderstand how could it happen?
I don't have much media and I have checked with DUAnalizer that I've got:
100% for / 56GB
94% for home
where is other memory...It could possibly that I used memory 56GB but not 200GB. :/

---

### Post by geltonas on 2009-03-14
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             178G   57G  113G  34% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  220K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  244K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volat

according perc 66% must be somewhere

---

### Post by ugm6hr on 2009-03-14
You have 2GB RAM.

Not much free.

This could be the problem, or your FF profile has corrupted.

Uncertain whether you can recover bookmarks etc, but to resolve it, you could just close FF, and delete the **~./mozilla/firefox** directory.

---

### Post by aextance on 2009-03-15
I've just had this same problem. According to Mozilla it's a problem with the places.sqlite file.

I removed the profile.ini file in /home/(user)/.mozilla and that got it working but that did lose my bookmarks.

The thread below might work better for you:

[http://ubuntuforums.org/showthread.php?t=793172]("http://ubuntuforums.org/showthread.php?t=793172")

---

