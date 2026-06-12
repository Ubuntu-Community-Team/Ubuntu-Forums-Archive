---
title: "How can I partition after Install?"
date: 2005-03-14
forum: Desktop Environments
---

### Post by RU63 on 2005-03-14
Hiya, 

I have a 60gb HD.  WHen i Installed UBUNTU months ago, I made a 20GB partition on /home/ (HDA3).  Now that partition is full.   I have 30GB free space on my main partition (HDA1).  I want to take that 30gb and make a new 15GB partition on /mnt/.  How can I do this without reinstalling Ubuntu?


Thanks,

---

### Post by Xian on 2005-03-14
[QUOTE=RU63]How can I do this without reinstalling Ubuntu?[/QUOTE]
I would just use the great Linux partitioning tool parted to get that set-up. There is a nice GUI called QTparted that you can run and make changes according to your needs. QTparted should be included in the available repos for Ubuntu.

---

### Post by rkn on 2005-03-14
To resize your / partition, it cannot be mounted.
Systemrescue:
[http://www.sysresccd.org/](http://www.sysresccd.org/)
Is a great bootable CD that has tons of tools including Qtparted which is very easy to use.

Bob

---

### Post by Xian on 2005-03-14
Or if like most people you have a Knoppix CD laying around that will also work.

---

### Post by az on 2005-03-14
...or the ubuntu live cd.

Or use the Warty installer to do your partitioning.  It works fine.  Just quit after you partition.

---

### Post by RU63 on 2005-03-16
[QUOTE=azz]
Or use the Warty installer to do your partitioning.  It works fine.  Just quit after you partition.[/QUOTE]

So, I won't lose my OS if i do this?

---

### Post by az on 2005-03-16
[QUOTE=RU63]So, I won't lose my OS if i do this?[/QUOTE]
Just do it right and do not create another filesystem on top.

---

### Post by RU63 on 2005-03-16
ok, i will try it on saturday. . . need time and I need to get the important files backed up before I try, just incase... ;)

---

