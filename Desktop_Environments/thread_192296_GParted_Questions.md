---
title: "GParted Questions"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Cable on 2006-06-08
First off, where do I start GParted?  I was able to start it using
```
gksudo gparted
``` 
but is there a way to start it using the menu?  Second, I was looking around in GParted just trying to get a feel for things.  How do I expand an extended partition?  I have my drive partitioned as follows:  Windows primary, Ubuntu primary, extended (/home, swap).  I'd like to expand that extended partition to add partitions to it.  How do I do that?  I have 188 gigs of unallocated space that I want to use.  :-P

---

### Post by aysiu on 2006-06-08
To see it in the menu, you might have to do ```
killall gnome-panel
```

As far as expanding the extended partition, can you post a screenshot of your GParted summary screen?

---

### Post by Cable on 2006-06-08
Here's the screenie...

---

### Post by aysiu on 2006-06-08
You can add to the end of a partition but not to the beginning of it.

In other words, you have two options:

1. Make your already big swap partition enormous.
2. Make the 188 GB unallocated space into another extended partition and then mount it as a data storage partition.

---

### Post by Cable on 2006-06-08
It won't allow me to create *another* extended partition...you can only have 1, can't you?  The option is grayed out when I right click and choose "New" and then click the dropdown menu for the choices of Primary, Logical, or Extended.  Do I need to deactivate/unmount my home and swap partitions first, then expand the current extended partition I have, then activate and remount the /home and swap partitions?

---

### Post by aysiu on 2006-06-08
Well, if it's greyed out in GParted, it could either be a GParted malfunction or the inability to have that many partitions. It's hard to tell.

---

### Post by Cable on 2006-06-08
If I right click on the extended partition and click information, its status reads "Busy (At least 1 logical partition is mounted).  Something tells me that the fact that the partitions within the extended partition are mounted makes it so I can't do anything with the extended partition until I unmount/deactivate those partitions.  But, I'm just taking a stab at what would make sense to me.  What do you think?

---

### Post by aysiu on 2006-06-08
Oh, so you're not using GParted from a live CD--you're using it from your installation?

---

### Post by Cable on 2006-06-08
Correct.  I didn't even think about that.  It'd probably work just fine if I used the live CD wouldn't it?  That way those partitions wouldn't be in use...

---

### Post by Cable on 2006-06-08
Got it, thanks.

---

