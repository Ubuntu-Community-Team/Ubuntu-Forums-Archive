---
title: "Partitioning probelm."
date: 2006-09-21
forum: Desktop Environments
---

### Post by alecjw on 2006-09-21
Hi. I want to repartition my hard disk. Curently it has the following partitions:
#1 15GB ext3 (ubuntu) | #2 10GB NTFS (windoze) | #3 Logical drive (160GB)

Within #3:
#6 157GB reiserfs (/home) | #5 3GB swap


What I want to do is to  shrink the Ubuntu partition down to 10GB and shrink the /home extended partition + logical drive adequately so that I can squeeze 2 more primary partitions into it:
#7 10GB ext3/reiserfs (Fedora Core/SuSE) | #8 10GB ext3/riserfs (gentoo)


Now, here's the probelem:
When I run Gparted from the livecd, it won't let me move the far left hand side of each partition, only the right. THis mesn that i get loads of little bits of free space spread out accross my hard disk, which I can't partition.

Anyone know how i can move the partitions left?
Thanks in advance.

---

### Post by wieman01 on 2006-09-21
Can you upload an **image of GParted**? It's easier this way. I am sure we can help, I have done similar stuff before (just recently to be precise) so I don't think this will be a big issue. But "seeing" it will be helpful. :-)

We'll have to do it step by step. To begin with, you can alway "capture" bits of free space by resizing the partition right next to it (on the left side).

---

### Post by alecjw on 2006-09-22
I've attached a screenshot. As you can see, I have 15GB in a logical drive and another 5GB drifting about between #1 and #2. I want 20GB of free space, all in one place (or 2 10GB's) But I can't seem to move the left hand side of each partition.

---

### Post by Old Pink on 2006-09-22
When you edit a partition, you'll have 3 editable fields:

Space to left
New size:
Space to right: 

Make sure the "space to left" and "space to right" are 0 in all cases, and you'll have no gaps.

---

### Post by alecjw on 2006-09-22
There isn't a space to the lieft option. It's greyed out. There's onlt size and space to right.

---

### Post by wieman01 on 2006-09-22
This is tough but manageable. First of all, let's try to get **hda1** and **hda2** closer together by moving **hda2** to the left.

1. Copy "hda2" to the unallocated space right of "hda6".
2. Delete "hda2".
3. Create a new partition left of "hda6".
4. Copy the previously moved partition on the right-hand side of "hda6" (previously "hda2") to the new partition next to "hda1".

Can you do that and confirm it has worked?

---

### Post by alecjw on 2006-09-22
I can't move the left hand side of a partition, only the right.

---

### Post by wieman01 on 2006-09-22
But you can copy & paste, don't you?

---

### Post by alecjw on 2006-09-22
Ok, thanks. I'll try that later whn i can be bothered to boot the livecd.

---

### Post by wieman01 on 2006-09-22
> **alecjw said:**
> Ok, thanks. I'll try that later whn i can be bothered to boot the livecd.
No problem. But this should work as I have done the same thing a couple of days ago...

---

