---
title: "What do you think of my swap partition?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by traveller on 2006-07-09
I installed Ubuntu on my Thinkpad the other day, I dual-boot with XP and here's the Partition List I have:

Partition 1

 /dev/hda1
Filesystem: Windows NTFS
Size: 30.50 GiB (7.34 GiB Free)

Partition 2

/dev/hda2
Filesystem: Extended 3
Size: 6:44 GiB (3.21 GiB Free)

Swap Partition /dev/hda5
Filesystem: Memory Swap
Size: 321.58 MiB

Partitions 1 and 2 are OK for now but what do you think of the swap partition? Is 321.58 MB enough space for it?

P.S.: RAM is 512 MB.

---

### Post by taurus on 2006-07-09
It should be enough if you have 512MB of RAM.  So, go for it...

---

### Post by traveller on 2006-07-09
> **taurus said:**
> It should be enough if you have 512MB of RAM.  So, go for it...
Thank you!

---

### Post by jgcamp99 on 2006-07-09
I've found that Ubuntu loves memory, the more you have the more generous the swap file size. Get 1.5-2 GB of ram and you'll probably never use swap.

---

### Post by Anduu on 2006-07-10
I have 1 Gig of ram and I think the highest I have ever seen my swap get was somewhere around 180 megabytes.

---

### Post by tturrisi on 2006-07-10
rule of thumb for swap is 1 to 1.5 times the amount of ram.  On a desktop this is way more than adequate but on a server w/ sql databases and/or multiple server side apps then 1.5x ram is best.  Also on a desktop, if doing lots of audio editing/burning or video editing/burning it's good to have that extra swap space.

---

### Post by Crosbie on 2006-07-10
And what happens when you upgrade your memory?

I have 512 of memory and 512 (or so) of swap space.  If I upgrade to a gig of memory is there any need to expand swap to match it?

---

