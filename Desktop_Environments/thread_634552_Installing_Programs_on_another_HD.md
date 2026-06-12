---
title: "Installing Programs on another HD"
date: 2007-12-07
forum: Desktop Environments
---

### Post by AdNZL on 2007-12-07
I'm using Ubuntu 6.06 and I was wondering if and how I could install programs on one of my other hard drives. 

Whenever I install anything with Ubuntu it defaults to installing the program and all its dependancies onto the same drive that Ubuntu is on. I only have about 500meg free on this drive, but I have a 200gig drive that is shared by Ubuntu and XP which has heaps of room left on it.

The 200gig drive is formatted in Ex3 and has does not have multipal partitions. I don't really want to have to move Ubuntu onto this Drive if there is a reliable way to make this drive the default drive for installations. 

So far I've found nothing that gives me an option to install on other drives/directories and which is a little frustrating :P

---

### Post by Happy_Man on 2007-12-07
You could move /usr/bin and /bin onto the other drive... but then it would have to be plugged in all the time, otherwise your system would refuse to function. To do this, use the link about /home in my sig, only instead of moving /home, move /usr/bin and /bin. Remember to back up first... this could presumably break your system.

---

### Post by AdNZL on 2007-12-07
Thanks heaps Happy Man :)

I'll have to try that later on this weekend.

I guess, by that reply, that there is no way to chose where you install programs except to move the directory to another drive?

For instance with XP the default directory for istalling programs is usually on C drive in Program files, but most Programs will ask you where you want to install them, and I would be able to chose from any drive and any directory within that drive providing I have enough space.

Can I do that with Ubuntu or am I stuck with just the one Directory? (not nessaserily a bad thing, but I'm curious).

---

### Post by Happy_Man on 2007-12-08
Well, you could, but only if you are installing from source. If you are using .deb's, I'm not sure whether you could or not.

---

