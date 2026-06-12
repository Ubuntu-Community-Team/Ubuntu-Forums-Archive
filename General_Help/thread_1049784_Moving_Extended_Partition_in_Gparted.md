---
title: "Moving Extended Partition in Gparted"
date: 2009-01-24
forum: General Help
---

### Post by mondayrocks on 2009-01-24
I'm trying to create a partition specifically for my home and I have two spaces of unallocated space that I would like to combine into one chunk. For some reason, however, I can't move the extended partition that combines my main Ubuntu partition and swap position to the right the six gigs to combine two unallocated spaces. There simply is no option in the liveCD version of GParted that allows for move/resize. 

I read somewhere that I have to delete the swap section in order to move it, but the instructions most everywhere seem to disregard this problem. Is it a problem? What can I do?

For reference, here is the partition map:

/dev/sda1: Windows  something or other, 47.03 megs
/dev/sda2: Windows partition, 118.66 gigs
12.89 gigs of unallocated space
/dev/sda4: extended partition
...../dev/sda5: 46.62 gigs (main Ubuntu Partition)
...../dev/sda6: 2.04 gigs (swap drive)
6.05 gigs of unallocated space

---

### Post by dcstar on 2009-01-25
> **mondayrocks said:**
> I'm trying to create a partition specifically for my home and I have two spaces of unallocated space that I would like to combine into one chunk. For some reason, however, I can't move the extended partition that combines my main Ubuntu partition and swap position to the right the six gigs to combine two unallocated spaces. There simply is no option in the liveCD version of GParted that allows for move/resize. 
.......

All partitions inside an Extended Partition have to be unmounted before you can do anything on the overall Extended Partition.

Use a Live CD and unmount anything inside the Extended Partition.

---

### Post by mondayrocks on 2009-01-25
Yea. I was doing this off the live cd.

---

### Post by -kg- on 2009-01-25
> **mondayrocks said:**
> I'm trying to create a partition specifically for my home and I have two spaces of unallocated space that I would like to combine into one chunk. For some reason, however, I can't move the extended partition that combines my main Ubuntu partition and swap position to the right the six gigs to combine two unallocated spaces. There simply is no option in the liveCD version of GParted that allows for move/resize. 

I read somewhere that I have to delete the swap section in order to move it, but the instructions most everywhere seem to disregard this problem. Is it a problem? What can I do?

For reference, here is the partition map:

/dev/sda1: Windows  something or other, 47.03 megs
/dev/sda2: Windows partition, 118.66 gigs
12.89 gigs of unallocated space
/dev/sda4: extended partition
...../dev/sda5: 46.62 gigs (main Ubuntu Partition)
...../dev/sda6: 2.04 gigs (swap drive)
6.05 gigs of unallocated space

If I understand what you're trying to do, you want to create a separate /home partition.  You can create that partition inside of the extended partition.

You will probably want to expand your Extended partition both ways to take up the remaining free space available, shrink your main Ubuntu partition to a smaller size, then create your /home partition in the space remaining inside the Extended partition.

In order to allow you to resize your Extended partition, you need to make sure that all the logical partitions are unmounted.  I'm not sure about the Ubuntu Live CD, but you might consider downloading the iso for the [GPartEd Live CD.]("http://gparted.sourceforge.net/")  This Live CD is set up specifically for partitioning, and does not mounted any of the partitions.  You should be able to unmount any mounted partitions in the Ubuntu Live CD partition editor, though you might have to do it manually.

For more information on partitioning operations, see [How To Partition.]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by TheViLliN on 2009-01-25
You need to expand the "Extended" partition to encompass the unallocated space first.  Then move your file system(ext3)/swap-file(linux-swap)partitions with in the extended partition. Then ncrease or decrease each file system partition as required.

Right click the "extended" partition (sda4 in your case) from the list of partitions first, not the graphical representation at the top because the unallocated space is not inside the extended partition.

And yeah.  Remove the swap partition temporarily until you get the partitions to the sizes you want the then make a new swap file at the end of the drive inside the extended partition.

Providing you are using the Live CD so all the partitions are unmounted.

---

### Post by unix1980 on 2009-01-25
I read somewhere that there is a bug in Gparted on the ubuntu livecd that prevents resizing/moving of extended partitions.  Download the SystemRescueCD and try the version on it.  I had a problem with resizing an extended partition with the livecd and Gparted on the SystemRescueCD worked flawlessly.

---

### Post by vahnx on 2009-02-28
I would also like to know the answer to this. Here's a link to my post about this same issue: [http://forums.fedoraforum.org/showthread.php?t=215240]("http://forums.fedoraforum.org/showthread.php?t=215240")

---

### Post by LordKelvan on 2009-11-01
Not sure if you still need help with this, but I ran into the same problem.  I had unmounted all the logical partitions in the extended partition, but GParted still didn't let me resize/move the extended partition.  It turns out that I had neglected to turn the swap partition (in the extended partition) off, and so it considered the swap as mounted.  So just right-click the swap partition, and select "Swapoff".  Then you should be able to resize/move the extended partition.

---

