---
title: "Is there any way to merge two partitions without formatting?"
date: 2009-02-06
forum: General Help
---

### Post by kapok on 2009-02-06
one is an ubuntu install, the other is blank.
is there any way of merging the blank one onto the end of the other without formatting?

seagate SATA 500g hard drive, split into 2 250g partitions. i would very much like all 500gs to be under ubuntu.

---

### Post by HermanAB on 2009-02-06
Some file systems like NFS can glue drives together.

Cheers,

Herman

---

### Post by hikaricore on 2009-02-06
Honestly your safest bet all around would be to transfer your important data to another drive and start fresh.

However.... if you wish to take the (very low) risk of dataloss you can boot from a livecd, delete the blank partition, and resize your main partition to file the space.  This is most easily done when the free space is at the end of the drive but can be done either way with some extra work.  This is fairly reliable and I done it dozens of times but just be aware there is some risk.

---

### Post by kapok on 2009-02-07
thanks man.
i'm going to back up all of the important stuff and then go for it.

edit: have to go borrow a friend's external hard drive; he's not awake yet. it'll be a few hours.

wish me luck. i'll post back here upon success or failure.

---

### Post by kapok on 2009-02-07
i can delete old partitions but i see no way of merging the new unallocated space onto the end of the old partition.

suggestions?

---

### Post by mikethehard on 2009-02-07
how are the partitions formatted just now?

as HermanAB said, some file systems can and some can't.

I was trying to do the same thing this week with FAT32 partitions and the most straight forward way was eventually to just copy the data to another drive and reformat the whole drive/unallocated space then transfer back to the new ext3 space - this method has the added bonus of 100% no data loss, guaranteed ;)

---

### Post by louieb on 2009-02-07
Sure its possible to grow a partition into unallocated space. It would help if you could post a screen-shot of the gparted window (alt+prtScrren will capture just the widow). 

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by dcstar on 2009-02-07
> **kapok said:**
> i can delete old partitions but i see no way of merging the new unallocated space onto the end of the old partition.

suggestions?

You cannot change mounted partitions, boot off a Live CD and use the Partition Manager.

---

### Post by kapok on 2009-02-07
i tried it from a live cd; i successfully deleted the one i want merged to the one i use, but when i tried to change the one that i want enlarged, it was automatically reset to its size.

---

### Post by Trim0 on 2009-02-07
> **kapok said:**
> one is an ubuntu install, the other is blank.
is there any way of merging the blank one onto the end of the other without formatting?

seagate SATA 500g hard drive, split into 2 250g partitions. i would very much like all 500gs to be under ubuntu.

do you use vista?

---

### Post by kapok on 2009-02-07
no, i do not use vista. i only have one hard drive; one half is ubuntu and the other is blank.

---

### Post by hellion0 on 2009-02-07
I'll have to second the "backup then repartition the partition you want to "grow" and the "blank" into a single partition at the size you want" suggestion.

---

### Post by kapok on 2009-02-07
how would i get my hard drive contents back onto the disk? can i just copy/paste from the live cd?

---

### Post by hikaricore on 2009-02-07
After you resized the partiton did you hit the Apply button?

This is required for all nearly all actions in gparted.

---

### Post by kapok on 2009-02-08
no; should i apply the deletion of the partition i want merged, and than resize the other?

i tried to do both in one go.

---

