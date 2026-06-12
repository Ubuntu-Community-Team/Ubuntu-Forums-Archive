---
title: "Missing disk space"
date: 2009-06-14
forum: General Help
---

### Post by VanillaMozilla on 2009-06-14
Take a look at this.  This is my Linux partition.

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb2             36993800  28021828   7092772  80% /


Out of 37 GB on the Linux partition, it shows 28 GB as used.  But only 10 GB are used and accounted for, as follows.

/home/  5.2 GB
/usr/   2.8 GB
/lib/   422 MB
/var/   726 MB
other  1306 MB

Any idea where the missing disk space might have gone?  Is this some kind of new math?


Here's the rest of the df output (sorry it's nearly illegible on the forum).

tmpfs                   189524         0    189524   0% /lib/init/rw
varrun                  189524       220    189304   1% /var/run
varlock                 189524         0    189524   0% /var/lock
udev                    189524       152    189372   1% /dev
tmpfs                   189524        88    189436   1% /dev/shm
lrm                     189524      2392    187132   2% /lib/modules

[edited to remove two external disks]

---

### Post by VanillaMozilla on 2009-06-14
[Edit--disregard this post.  It includes 11 GB in two external disks, which just adds to the confusion.]


Here's a different way of looking at it.  Using the file browser, I right click on the File System.  It says 311,267 items, totaling 21.0 GB (some contents unreadable).  But when I right click on each of the directories they total only 10 GB, as detailed above--not 21.0.  It also says 6.8 GB free space, out of a 37 GB partition.

It also shows a /media/ directory with 11.4 GB.  But all of that is on two other disks!  So where did all my space go?

---

### Post by lisati on 2009-06-14
Hidden files?

---

### Post by VanillaMozilla on 2009-06-15
> **lisati said:**
> Hidden files?
Good idea, but no.  Sorry, no, there are almost no hidden files.

Update:  File Manager shows a total of 9.8 GB, with or without hidden files.  But there is still only 6.8 GB free out of a 37 GB disk.  df shows 28 GB used, not 10.

Could this be the difference between allocated space and actual space used?  Geesh.  That's pretty extreme.  What gives?  This disk shouldn't be full.

---

### Post by VanillaMozilla on 2009-08-29
Problem solved.  Posting the answer for others to see.

The Properties view is totally misleading.  Apparently it does not include hidden files even if you have hidden files displayed.

I found 16.5 GB in /home/my account/.local/share/Trash , but the Properties display apparently does not include that in the total.  It does show 16.5 GB if I drill down to /home/my account/.local .  

The Properties view is not only inaccurate, but also very slow.  I don't recommend it for summarizing disk usage.

Use the Disk Usage Analyzer instead.  It's hidden under Applications, not under System Administration where you would expect it.

---

### Post by VanillaMozilla on 2010-03-12
Update:

There's a bug report somewhere about Nautilus and other tools not displaying files with a hidden directory in the path.  Sorry, I don't have the number.

---

### Post by audiomick on 2010-03-12
> **VanillaMozilla said:**
> 
Here's the rest of the df output ([COLOR=Red]sorry it's nearly illegible on the forum[/COLOR]).

tmpfs                   189524         0    189524   0% /lib/init/rw
varrun                  189524       220    189304   1% /var/run
varlock                 189524         0    189524   0% /var/lock
udev                    189524       152    189372   1% /dev
tmpfs                   189524        88    189436   1% /dev/shm
lrm                     189524      2392    187132   2% /lib/modules

[edited to remove two external disks]
just for the record, since you mention it, if you use the # button at the top of the posting window to put code tags around the text, it looks like this
```
tmpfs                   189524         0    189524   0% /lib/init/rw
varrun                  189524       220    189304   1% /var/run
varlock                 189524         0    189524   0% /var/lock
udev                    189524       152    189372   1% /dev
tmpfs                   189524        88    189436   1% /dev/shm
lrm                     189524      2392    187132   2% /lib/modules
```

---

### Post by VanillaMozilla on 2010-03-14
Thanks for mentioning it.  Alas, every forum works differently, and life is too short to find all the inscrutable icons for all of them.  Maybe I'll be able to find it the next time.

---

