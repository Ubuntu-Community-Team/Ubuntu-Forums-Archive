---
title: "Lost Ubuntu"
date: 2009-05-25
forum: General Help
---

### Post by marveroluis on 2009-05-25
Installed Ubuntu 9.04 32 on a HP running AMD 64, from a CD.
All was well, getting email, firefox add-ons, etc. Finally decided to download Skype and all hell broke loose...Was unable to uninstall Skype and Firefox mentioned that I was out of memory...
When I tried to reboot both with Ubuntu and Ubuntu recovery, the final line reads:
Kernel panic, not syncing: attempted to kill init!
Can I reinstall from the CD or do I have to do something before that.
By the way Vista premium is working fine.
Thanks a million.
Luis :(

---

### Post by 73ckn797 on 2009-05-25
Did you install Skype from the repositories (Synaptic Package Manager) or from their web site?

---

### Post by marveroluis on 2009-05-25
thanks, installed from their web site

---

### Post by dragos_iliescu_2005 on 2009-05-25
Try to reinstall on clean partition. How much swap you have? Minimum 1 Gb. I'll say.

---

### Post by marveroluis on 2009-05-25
Not sure what do you mean by swap...
I will do as you suggest.
What happens to the partition that is not working?
Also if the problem was running out of space, how do I partition more?
Thanks

---

### Post by dragos_iliescu_2005 on 2009-05-25
Swap is a special partition type used by the system when your RAM is not enough. It is used as RAM.
Tipically min. 1Gb but it's depending on your RAM size.
Regarding the hard size for Ubuntu: what size do you have?

---

### Post by dragos_iliescu_2005 on 2009-05-25
Reffer to the attached file for swap...

---

### Post by marveroluis on 2009-05-25
> **dragos_iliescu_2005 said:**
> Reffer to the attached file for swap...
thanks Dragos for the help, not sure what the size is for Ubuntu on the hard drive, did not write it down when I installed it and I am not sure how to look at the partitions outside of windows.
I do have 4 gb of Ram, will explore the meaning of the swap you send me, sorry just beginning...

---

### Post by dragos_iliescu_2005 on 2009-05-25
If you have 4 Gb, forget about swap. You problem come from other source I presume. I'm not sure about. However, a clean install may solve your problem. Good luck.

---

### Post by marveroluis on 2009-05-25
Thanks Dragos, will try the clean install, nevertheless I am downloading the g-parted.
Thanks again

---

### Post by dragos_iliescu_2005 on 2009-05-25
Before install, run memtest. Just in case.

---

### Post by marveroluis on 2009-05-25
Dragos, I did and there was no problem, one last quick question, does g-parted run in windows or only in linux?
Thanks again
Luis

---

### Post by marveroluis on 2009-05-25
Dragos, probably you are fast asleep...,may be tomorrow, I did reinstall Ubuntu, know I have two sets of three ( Ubuntu, recovery and memtest), one working the other totally screwed up, ( would love to get rid of it) As I started working on the newly installed, i got the no more memory pretty fast, when I checked the partition is only 2.3 GB with aprox 600 MB free, how can I expand the capacity of the partition. Thanks

---

### Post by dragos_iliescu_2005 on 2009-05-26
Back again.
GParted is only for linux

run 'fdisk -l' in terminal as root and post here the result. However, you should make a plan how to partition your hard disk.

Take a look at this link about partitioning.
I'll try to help you on this issue.

---

### Post by marveroluis on 2009-05-26
> **dragos_iliescu_2005 said:**
> Back again.
GParted is only for linux

run 'fdisk -l' in terminal as root and post here the result. However, you should make a plan how to partition your hard disk.

Take a look at this link about partitioning.
I'll try to help you on this issue.

Hey Dragos, nice to hear from you again, will try the fdisk, I am on Vista as Ubuntu with the 2.3 GB of partition is not working well. The link you mentioned did not come thru in your last post.Thanks

---

### Post by marveroluis on 2009-05-26
l@l-laptop:~$ fdisk - 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by dragos_iliescu_2005 on 2009-05-27
Sorry for the broken/ missing link.
Command I sugegest you to use was fdisk -l (l from "list").
As I understood till now, you have one Vista partition and two Ubuntu partitions.
If I understood well, please confirme here.
If this is the case you need to delete these two Ubuntu partitions and format a new and a clean one.

---

### Post by dragos_iliescu_2005 on 2009-05-27
You can read about manual (advanced) partitioning here:

[http://mywebsite.bigpond.net.au/dfelderh/p23.html]("http://mywebsite.bigpond.net.au/dfelderh/p23.html")

---

### Post by marveroluis on 2009-05-27
This is what I have: two vista premium partitions, a main one and a small with recovery info in case of a crash.
Now I also have two ubuntu partitions, the one that crashed and the one I reinstalled as per your suggestion. I would definitely like to delete this two partitions ans start from scratch, but don't know how to go about doing it, may be is on the link you suggested I read. I am at work now so with no access to my computer. I appreciate your help and please forgive my ignorance, definitely willing to learn.

---

### Post by marveroluis on 2009-05-27
I will try the l from list as soon as I get home...

---

