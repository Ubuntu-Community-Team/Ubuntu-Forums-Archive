---
title: "my partition set up- HELP"
date: 2006-03-15
forum: Desktop Environments
---

### Post by stabface on 2006-03-15
[HTML]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb1              3842376   3348128    299060  92% /
tmpfs                   388276         0    388276   0% /dev/shm
tmpfs                   388276     12588    375688   4% /lib/modules/2.6.12-10-386/volatile
/dev/hdb3             70769848   9418896  57756008  15% /home
/dev/hda2             20472848    540928  19931920   3% /media/hda2[/HTML]


here is what i get when I type DF in term. 

here is my question, the other day i had a problem after upgrading that my root partition filled up and x would not boot. i have 50 extra gigs on my home partition. what should i do to avoid that. Either set it up so when i get new packages or upgrades they go to home and not root or make root bigger.

---

### Post by yomam1 on 2006-03-15
resize your root & home partition give urself room. thats just my opinion though

---

### Post by stabface on 2006-03-16
can i just pop in the live disk and use gparted and resize the partition? 
or do i have to get all linuxy and create new partitions and blah blah?
what are my chances of screwing something up and ruining my system?

---

