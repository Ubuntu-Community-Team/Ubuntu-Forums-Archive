---
title: "Gparted issue?..."
date: 2005-11-29
forum: Desktop Environments
---

### Post by yeahyeahyeah on 2005-11-29
So last weekend I installed Ubuntu on my laptop that had XP. It dual boots, etc, just fine. 

When I installed Ubuntu, I used the install to shrink the 100GB disk XP was on to a 70GB NTFS partition. Then I created a 24GB ext3 root partition for Ubuntu, as well as a 1GB ext3 swap for Ubuntu. The remaining small amount of space that was left, I turned into a FAT32 partition.

Today I decided I really don't need 24GB for Ubuntu, so I wanted to shrink that to 15GB and increase my XP partition to 80GB.

I ran into a problem using GParted from within Ubuntu, since all the disks were locked, so I read and learned that I needed to boot from a Ubuntu Live CD so the disks would not be mounted.

I did that, but the swap file disk still had a lock, and trying to shrink the root partition from 24GB to 15GB resulted in a long wait, then a message from Ubuntu that one of the operations included a busy resource. So I read some more, and found that a locked swap partition can cause that.

So I did a swapoff -a, and that removed the lock next to the swap partition. At this point, none of the hda's were active or busy...but GParted STILL does not shrink the root partition. Now there is still that long wait, but afterwards no message and the partition is still 24GB.

Any suggestions? Thanks in advance.

---

### Post by aysiu on 2005-11-30
The live CD may, in fact, be using the swap space--maybe that's why it can't resize it.

GParted and QTParted and competent partitioning tools. However, I have found them to not be 100% reliable. The best (free) partitioner I've ever used is Mandriva's DiskDrake.

Just get the first CD of Mandriva, pretend to install it--right up to using the partitioning tool--then, force your computer to reboot after resizing the appropriate partitions.

---

### Post by yeahyeahyeah on 2005-12-01
The live CD does use the swap space.

I disabled that by swapoff -a, so none of the drives were locked or busy.

Still a no-go.



[QUOTE=aysiu]The live CD may, in fact, be using the swap space--maybe that's why it can't resize it.

GParted and QTParted and competent partitioning tools. However, I have found them to not be 100% reliable. The best (free) partitioner I've ever used is Mandriva's DiskDrake.

Just get the first CD of Mandriva, pretend to install it--right up to using the partitioning tool--then, force your computer to reboot after resizing the appropriate partitions.[/QUOTE]

---

