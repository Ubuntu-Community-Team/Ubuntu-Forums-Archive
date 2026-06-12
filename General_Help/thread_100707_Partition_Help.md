---
title: "Partition Help"
date: 2005-12-08
forum: General Help
---

### Post by bananaman on 2005-12-08
Ok here we go...

I installed Ubuntu less than a week ago, i partitioned my hard drive and gave Ubuntu a 6 gig partition...

I liked Ubuntu so much i decided to ditch most of windows and resized the partitions so that Ubuntu would now have 15 gigs...

The problem is now, after only a couple of days, its telling me that out of those 15 gigs I only have 3 left (thats what i get in Nautilus)...
But if I go to System Monitor and check the Devices tab... it tells me my Ubuntu partition has a total of 6 gigs and 3 left which makes much more sense...

The problem is (i think) somehow the partition did grow, and at least nautilus is recognizing it, but the system still sees it as a 6 gig partition with 3 free... Nautiuls tells me its a 15gig partition with 3 free...

I hope I've made myself clear, if you can please help me maybe im missing something is should have done when i resized the partitions...

By the way i used a windows program to partition and resize the partitions...
Thanks in advance...

---

### Post by fourchannel on 2005-12-08
what does
```
df -h
```
say?

---

### Post by az on 2005-12-08
How did you resize the partition?

You may have resized the partition, but not the filesystem on it.

---

### Post by bananaman on 2005-12-08
Yes, you are both right...

df -h      says

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             6.1G  3.0G  2.9G  52% /


So yes, i think the problem is that i didnt resize the file system...
how do i go about doing that?

thank you

---

### Post by Bachstelze on 2005-12-08
Partition resizing is always a difficult matter. The most simple way would be to format everything... If you don't want to format, boot from a Live CD and hope it works.

---

### Post by bananaman on 2005-12-08
ok so i boot from the cd and then what?
please help me i really really really dont want to format...

thank you for your help

---

### Post by Bachstelze on 2005-12-08
Boot from the live CD and run the partitioning tool (QTParted under Knoppix, I don't know if the Ubuntu live CD has one). Then you have a graphical interface which is pretty intuitive, right-click on your partition, choose "Resize" and hope it works.

---

### Post by bananaman on 2005-12-08
alright...ill try that...

but the partition is already resized...what i need is to resize the file system...that should do it?

---

