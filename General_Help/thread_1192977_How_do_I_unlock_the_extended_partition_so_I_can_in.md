---
title: "How do I unlock the extended partition so I can increase Ubuntu's partition size?"
date: 2009-06-20
forum: General Help
---

### Post by Blue Dolphins on 2009-06-20
Even though I'm using a live CD and the harddrive is unmounted, I can't unlock the extended partition.  I used to duel boot with windows XP, but not anymore, and I want to increase xubuntu's partition size to reclaim all of that extra space.  

What do I need to do to unlock the extended partion?

---

### Post by michy99 on 2009-06-20
I'm not sure what you mean by 'unlock.' You should be able to enlarge the partition and then enlarge the partition inside, assuming there is free space to expand into, and that the partitions are not mounted.

Perhaps a screenshot from Gparted would help.

---

### Post by plucky on 2009-06-21
> **Blue Dolphins said:**
> Even though I'm using a live CD and the harddrive is unmounted, I can't unlock the extended partition.  I used to duel boot with windows XP, but not anymore, and I want to increase xubuntu's partition size to reclaim all of that extra space.  

What do I need to do to unlock the extended partion?

Turn swap off.The Live CD mounts the swap partition,which I assume is in the extended partition,and that causes the extended partition to be locked.

Select the swap partition and right click.Then select swapoff.

Good Luck

---

