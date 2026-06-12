---
title: "Resizing Root partition question - how safe?"
date: 2008-12-23
forum: General Help
---

### Post by 3pinner on 2008-12-23
How safe is it to resize the / partition using Partition Editor (GParted)?
My /home and /swap are on seperate partitions. I will be installing 8.10 over the existing installation.
the / partition is 93 Gb, and I really don't think it needs to be that big, so I want to shrink it down to 10 Gb or so.

this system is currently dual boot with Windows on a seperate hard disk, and GRUB as my boot loader.

Any potential problems here?

Thanks!

---

### Post by Titan8990 on 2008-12-23
Always potential for problems when dealing with partitions, BACKUP first.

---

### Post by bodhi.zazen on 2008-12-23
Although problems are rare they can happen. Back up first.

And to resize / you need to use a live CD.

---

### Post by hyper_ch on 2008-12-23
in addition: make sure you have always current backups. You never know what happens. A drive may just fail from one day to another.

---

### Post by 3pinner on 2008-12-23
thank you for the replies.
I have backed up my /home partition.
I will be installing 8.10 in the / partition to replace my current 7.10
Can I just resize the partition when I get to that part of the install process?
And as for the /home partition, do I just mount it (not format it) so the new OS will recognize it as the /home partition?

Thanks!

---

### Post by mike555 on 2008-12-23
You may run into problems if you use your old Home folder without formatting, if it has settings and set-ups for an older system (hidden files)....

---

