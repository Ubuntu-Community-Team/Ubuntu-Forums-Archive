---
title: "fsck required every other day :("
date: 2009-02-01
forum: General Help
---

### Post by iitkian on 2009-02-01
Hi,

I am new to ubuntu. Love the environment, but the every other day the bootup says: Routine check, followed by Automatic fsck check failed. The computer moves to an unmounted stage, and asks for manual fsck.

Is this a hard drive error, or is there some problem with my CD?

Tried installing a few times, with the same results always :(

I have Ubuntu 8.04 LTS

TIA

---

### Post by cb951303 on 2009-02-01
since fsck fails it's normal that it tries to check everyday.
when it happened to me a manual fsck check got rid of it. but it may also be a harddisk problem.

---

### Post by ajgreeny on 2009-02-01
Boot your ubuntu live CD, and from that with no hard disk partitions mounted run ```
sudo fsck /dev/sdx#
``` where sdx#is your apparently faulty ubuntu partition, eg sda2 in my case where it is the second partition on my first hard disk, windows being the first partition.  That may well solve your problem, but if it carries on, it could be a disk about to fail, so make sure you are well backed up, and be prepared for the disk to fail completely.  Let's hope it's just a minor filesystem problem and the manual fsck stops it.

---

### Post by x33a on 2009-02-01
to make sure that your hard drive isn't having any bad sectors, download system rescue disc or a similar rescue disc, and use the tools provided within to thoroughly check your hard drive. after then proceed with the installation.

---

### Post by SunnyRabbiera on 2009-02-01
Well Ubuntu usually checks itself every 20-30 boots or so (I have seen it vary)
How often do you turn on and off your computer?
Do you dual boot?

---

