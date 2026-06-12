---
title: "Ubuntu 7.10 can't resize windows partion"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by dicecca112 on 2007-10-18
Can't do it in either the Text only of 7.10 install or in Windows Vista itself via Adminstrative tools.  I've been able to do it in the past.    

Hardware is a Dell 1520 Laptop

I don't quite remember the error, but it just said it encountered an error and could not continue.  There is only one partition on this disk, and it has vista on it. 


Gonna try GParted and see if I can get that to work.

---

### Post by wjp.reg on 2007-10-18
> **dicecca112 said:**
> Can't do it in either the Text only of 7.10 install or in Windows Vista itself via Adminstrative tools.  I've been able to do it in the past.    

Hardware is a Dell 1520 Laptop

I don't quite remember the error, but it just said it encountered an error and could not continue.  There is only one partition on this disk, and it has vista on it. 


Gonna try GParted and see if I can get that to work.

did you defrag vista first?

---

### Post by sebald on 2007-10-18
Defrag first is a good suggestion. I had a scary situation on my 1420 where no installer would see the partitions on my disk (previously partitioned with ext3 and swap) - the Vista partitioner saw some kind of error... so I removed the Linux partitions and some of those little Dell utility partitions, then it could find the free space and use it. Scary. 

I know the first time I resized the huge Vista partition it would only shrink down to 60 MB or so  (I did it in Vista) - dunno what it saw that kept it that big.

---

### Post by zorkerz on 2007-10-20
Ive had this problem on two computers. Gparted seems to be unable to resize my vista ntfs partitions often. I have done defrags and full disk scans all through vista and gparted still will not allow me to resize (with the partition unmounted).

Vista has a resizing tool that works ok but it does not allow it to go too small. I have a 23 gig vista partition with i think almost 10 gigs free but vista will not allow it any smaller. This is much to big for me as its 23% of my hardrive and i use it less than once a month.

Has anyone else had this problem?

---

### Post by kamaboko on 2007-10-21
This is just a thought, but have you decreased the size of your Vista shadowdrive before partitioning?

---

