---
title: "Do I need swap"
date: 2008-03-13
forum: Desktop Environments
---

### Post by oddworld on 2008-03-13
Ive got 2 gigs of ram on by Gutsy, so I really need swap?
I know how to remove it, but whats the point in having swap if you have a lot of memory?

---

### Post by mcsimon on 2008-03-13
Just in case you need more ;)

---

### Post by kerry_s on 2008-03-13
> **oddworld said:**
> Ive got 2 gigs of ram on by Gutsy, so I really need swap?
I know how to remove it, but whats the point in having swap if you have a lot of memory?

no, not really, but some programs are made to use swap, they are few though. if you got space just leave it or make it small. it's up to you.

---

### Post by oddworld on 2008-03-13
Yea Ive got 2 gigs of ram, and 2 gigs of swap.
However I have never used more than 600mb combined at any point.
BTW hibernate does not work on laptop anyways, no using it there.
O well

---

### Post by |{urse on 2008-03-13
lol i've always wondered this too. on my fedora box i have 4gb of ram and when i partition i like nice round numbers and was left with a small sda3 partition mkswap /dev/sda3 (sda3 was about 29mb in size lol) and that system rocked hard ^^ i recently repartitioned out a nice 2gb swap file and i see absolutely no difference in performance. Go figure:popcorn:

---

### Post by daengbo on 2008-03-13
Swap is a safety net. With 2GB RAM, you'll probably never need it. Let's be honest, though -- will you really miss that 1GB on your 500GB drive? Also, if you plan to hibenate, you'll need at least as much swap as physical memory.

---

### Post by sandysandy on 2008-03-13
> **daengbo said:**
> Swap is a safety net. With 2GB RAM, you'll probably never need it. Let's be honest, though -- will you really miss that 1GB on your 500GB drive? 

second that

regards

---

### Post by oddworld on 2008-03-13
Well I will miss those 2 gigs on my disk.
Its a 60 gig HD laptop with 3 partitions.
1 for XP (I need some engineering apps that don't work at all with WINE)
2 for a FAT32 partition for data that both OS can read
3 for ubuntu
So the 2 gigs of swap are sorta alot.
I dont feel like removing it because everything is working well and I don't want to FUBAR myself.

---

