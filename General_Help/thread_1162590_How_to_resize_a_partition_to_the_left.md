---
title: "How to resize a partition to the left?"
date: 2009-05-17
forum: General Help
---

### Post by bike756 on 2009-05-17
So I had windows on my computers first partition for a while, but then deleted it after I realized how crappy windows is. Now I am left with 30 gigs of empty space in front of my Ubuntu partition. 

How can I expand the second partition to the left? I want one big partition with just the swap after it.

I have tried the Gparted live cd with no success. It won't let me drag it to the left, unless there is something I am doing wrong. 

I have attached a small screenshot of the partitions from gparted.

Thanks!
Nate

---

### Post by taurus on 2009-05-17
You need to run gparted from either Ubuntu LiveCD or GParted LiveCD.  Make sure all the partitions are not mounted.  Then, delete /dev/sda1 (is that what you want, deleting windows from the first partition?).  Now, expand /dev/sda2 to take up that unallocated space.  Then, expand /dev/sda5 to take up that new space.

Write to disk and reboot.

---

### Post by bike756 on 2009-05-18
Thank you!

I can't believe it took me as long as it did to figure that out. 
I had been trying to expand sda5 without expanding sda2 first. Still not sure I understand why there is a partition inside a partition, but I got it to work, so that is good enough for now :)

---

### Post by CatKiller on 2009-05-18
Contrast Extended partitions with Primary partitions.

You can only have four Primary partitions on a drive. If you could only have Primary partitions, you'd only ever be able to have four partitions. If, instead, one of those Primary partitions could hold other partitions, you could have a much larger number. That's the Extended partition, and it's been around for quite some time.

---

### Post by bike756 on 2009-05-18
That makes perfect sense :)

What a helpful forum! Thanks!

---

