---
title: "Ubuntu - question about partitions"
date: 2009-02-07
forum: General Help
---

### Post by zocky on 2009-02-07
Hello!

I right now don't know much about linux in general, but was thinking of giving it a try. I'd install it besides my Windows XP, which are running on C partition.

But before i install it, i have one question.
Right now, i have partitions C, D and E. Windows runs on C, while D and E is just for apps, games, etc.

I was thinking of installing ubuntu on D partition (it hs NTFS system), but i don't  wanna format and therefor loose all files (and apps, games, ...) on that partition. Is it possible to install ubuntu on D disk, but without formation that partition and loosing all files on it? Like you would install regular app? Or do i have to delete/format everything on that partition, if i want to install ubuntu there?

And also, i have lot of free space on D partition. Is it possible to divide/separate D in 2 partitions the way, that all all data that is currently on D drive, would remain on it, and from the empty D drive, it would create new drive/partition?

Sorry if this sound noobish, but i need to know that before i install Ubuntu (which i would really like to try).

Tnx for any help! :)

---

### Post by 73ckn797 on 2009-02-07
You can install in many was and not lose data. I recommend you look at the Community Documentation or search the forums to find the info you need first.

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by Sidewinder1 on 2009-02-07
I do believe that you can do that. I would defragment all drives (partitions) especially D; then running from "live cd" use the partition editor (believe that it's still Gparted) and resize (shrink) the NTFS portion of D:, don't make it smaller than it's data block size; then format the "unallocated" space to ext3 for your linux installation. I'll let some one else chime in about swap and extended partitions.
Hope this helps.

---

### Post by drs305 on 2009-02-07
> **zocky said:**
> 
And also, i have lot of free space on D partition. Is it possible to divide/separate D in 2 partitions the way, that all all data that is currently on D drive, would remain on it, and from the empty D drive, it would create new drive/partition?


This would be your best option. Ubuntu will need a partition formatted for linux (ext3 or soon ext4). This formatting will destroy any data you have on that partition. You can split an existing partition and use the new space for your linux installation.

Some things to keep in mind:
Degrag your current partition to help minimize the chance of data loss.
Be sure to make backups of all your important data before doing any repartitioning.
You can create new partitions from within the ubuntu LiveCD by using an app called *gparted*. (System > Administration > Partition Editor). However, if you feel more comfortable with a windows partitioner do it from there before moving to the installation.

This site has a good discussion of planning your ubuntu installation:
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

---

