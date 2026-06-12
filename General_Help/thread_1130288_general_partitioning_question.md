---
title: "general partitioning question"
date: 2009-04-19
forum: General Help
---

### Post by scristopher on 2009-04-19
i just have a general partitioning question i have 2 partitions, using ubuntu as my main partition, i use to have vista on another partition but ended up getting rid of it now its just a 200 gb partition i would like to use it for ubuntu because my ubuntu partition is only 40gb is there any way i can just combine it w/ the ubuntu partition or if not use the 200gb partition when i start running out of space to install apps and packages on? any input is much appreciated thanx~!:KS

---

### Post by drs305 on 2009-04-19
Yes, you can use gparted to expand the ubuntu partition. You access gparted via System, Administration, Partition Editor (or *gksudo gparted* in a terminal). 

If the other partition still exists, you would delete it and then expand the ubuntu partition to absorb the free space. Any operation involving your system disk will have to be run from the LiveCD or third party CD such as the SystemRescueCD since you can't perform these operations on a mounted partition.

Personally, I would expand the system partition a bit if you feel like you need extra room and make an additional *logical* partition. Frist you create an extended partition and then create logical partition(s) within it. The advantage of having logical partitions (with an extended partition) is you won't be limited to only 4 partitions and can divide the extended partition  up into multiple parts in the future should you desire.

As with any partitioning, back up any critical data before proceeding.

---

### Post by scristopher on 2009-04-19
> **drs305 said:**
> Yes, you can use gparted to expand the ubuntu partition. You access gparted via System, Administration, Partition Editor (or *gksudo gparted* in a terminal). 

If the other partition still exists, you would delete it and then expand the ubuntu partition to absorb the free space. Any operation involving your system disk will have to be run from the LiveCD or third party CD such as the SystemRescueCD since you can't perform these operations on a mounted partition.

Personally, I would expand the system partition a bit if you feel like you need extra room and make an additional *logical* partition. Frist you create an extended partition and then create logical partition(s) within it. The advantage of having logical partitions (with an extended partition) is you won't be limited to only 4 partitions and can divide the extended partition  up into multiple parts in the future should you desire.

As with any partitioning, back up any critical data before proceeding.
thank you I believe the live cd should do the trick i was thinking of doing this but wasnt sure if it would destroy the system i currently have by exspanding the partition. but yes i would only like to have one partition i have no need for extra partitions (or other OS's at this time)

---

