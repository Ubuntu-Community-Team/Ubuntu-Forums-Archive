---
title: "New Install and Partitioning."
date: 2009-01-27
forum: General Help
---

### Post by Louie IV on 2009-01-27
Hello everyone,
     I am brand new to Ubuntu so I need some help with this partitioning business.  I have two Hard Drives. The first is a 74 gb drive and the other is a 400gb.
On the 74gb drive I have one 37997mb ntfs partition containing my XP OS which I want to keep for now. The rest of this drive is currently unpartitioned, but I want to install Ubuntu on it.  
When I create a partition from this leftover space I don't know how to fill out the very simple form,
 So I have the follow questions: 
           Should I select Logical or Primary? (My guess is logical.) 
           I Know the size.
           Should the location of the partition be at the beginning or the end?
           I assume Ext3 is the file system that Ubuntu loads on.
           And what of this Mount Point business?

I'm manually partitioning my drives.  I need to know exactly how to partition the rest of the 74gb drive in order to have both OSes running on it and use the 400gb drive for storage.

Thanks,
Lou

---

### Post by dcstar on 2009-01-27
> **Louie IV said:**
> Hello everyone,
     I am brand new to Ubuntu so I need some help with this partitioning business.  I have two Hard Drives. The first is a 74 gb drive and the other is a 400gb.
On the 74gb drive I have one 37997mb ntfs partition containing my XP OS which I want to keep for now. The rest of this drive is currently unpartitioned, but I want to install Ubuntu on it.  
When I create a partition from this leftover space I don't know how to fill out the very simple form,
 So I have the follow questions: 
           Should I select Logical or Primary? (My guess is logical.) 
           I Know the size.
           Should the location of the partition be at the beginning or the end?
           I assume Ext3 is the file system that Ubuntu loads on.
           And what of this Mount Point business?

I'm manually partitioning my drives.  I need to know exactly how to partition the rest of the 74gb drive in order to have both OSes running on it and use the 400gb drive for storage.


A "normal" drive can have 4 Primary partitions maximum, but if you have one logical partition there is no limit inside the logical partition - it is ok for you to make a Primary Partition.

I would recommend two partitions:

One 10G EXT3 Primary partition for the Ubuntu "/" (root) partition
One EXT3 Extended partition (however big you want) for "/home" (these are your user files/configuration).

You can use the other drive for storage as you have indicated.

I would recommend leaving at least 10G free for a future install, this means that you can have multiple versions available (if you want)

---

### Post by Louie IV on 2009-01-27
Thank you very much.  Does the location of the new partition matter? Beginning or End?

---

### Post by dcstar on 2009-01-27
> **Louie IV said:**
> Thank you very much.  Does the location of the new partition matter? Beginning or End?

Not really - unless you intend growing it later, then if there is adjacent free space to a partition it is a bit easier than moving partitions to create space.

---

### Post by theozzlives on 2009-01-27
> **dcstar said:**
> A "normal" drive can have 4 Primary partitions maximum, but if you have one logical partition there is no limit inside the logical partition - it is ok for you to make a Primary Partition.

I would recommend two partitions:

One 10G EXT3 Primary partition for the Ubuntu "/" (root) partition
One EXT3 Extended partition (however big you want) for "/home" (these are your user files/configuration).

You can use the other drive for storage as you have indicated.

I would recommend leaving at least 10G free for a future install, this means that you can have multiple versions available (if you want)

Don't forget one for swap the size of your RAM

---

### Post by Louie IV on 2009-01-27
Brilliant.  Thank you.

---

### Post by dcstar on 2009-01-27
> **theozzlives said:**
> Don't forget one for swap the size of your RAM

Oh yeah - put it in a logical partition (don't waste a Primary on it).

---

