---
title: "Divide disk for linux"
date: 2012-03-01
forum: Desktop Environments
---

### Post by Apostolus on 2012-03-01
HI,

I'm learning about hard drives and linux and I have questions. I divided disk into 6 partitions. Because you can't have 4 primary partition I divided disk like this:

/dev/sda1 (primary) for /root
/dev/sda2 (primary) for swap
/dev/sda3 (extended) and divided for 4 logical partition with the same size:
/dev/sda5 /home 
/dev/sda6 /tmp
/dev/sda7 /usr
/dev/sda8 /var

Questions:

Is this disk distributions alright?
How can I determin that /dev/sda3 is indicator of extended partition?
Why It skipped /dev/sda4?


Please forgive me for my english. Thank you for answers.

---

### Post by Rex Bouwense on 2012-03-01
I'm not sure why you did what you did but here goes;
sda1 through sda4 are primary partitions.  You have three primary partitions one of which is an extended partition with four logical partitions (5-8).
1.  Is it right?  Depends upon what you want to do.  I'm not sure why you have /tem, /usr, and /var on separate partitions.
2.  Look on Gparted and you will be able to see your partitions.
3.  Sda4 was skipped because you only created three three primary partitions.

---

### Post by Apostolus on 2012-03-01
Wow. Thank you for quick respond, now I'm much smarter :-) 

I read that this separation is good for managing system, but I guess that depends on user. Again thank you very much.

---

### Post by Rex Bouwense on 2012-03-01
Many people place /home in a separate partition to make it easier to do clean installs without losing their data/music/photos/etc.  Others use an external storage device and back up their stuff (daily, weekly, whenever).  Still others use a cloud.  Some people don't worry about it.  I for one believe that if you don't back up your data you really don't care about it because sooner or later you will lose it.
By the way welcome to the forums.  :popcorn:

---

