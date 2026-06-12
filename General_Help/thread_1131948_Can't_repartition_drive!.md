---
title: "Can't repartition drive!"
date: 2009-04-21
forum: General Help
---

### Post by Flexico on 2009-04-21
[--unallocated--][---ubuntu---][-swap-]

"Partition Editor" won't let me move my ubuntu partition left to fill the unallocated space! I boot from my USB startup drive so I can move the bootable partition, but even though I can resize the "right" side, the "left" side can't be moved. It's as if the empty space isn't there!

---

### Post by mwacky on 2009-04-21
You might need to boot up with the Live CD to resize your partition as it is effectively locked when you are running the OS from it.

---

### Post by Flexico on 2009-04-21
I did that! That's what I meant about the USB drive, I made a USB startup disk from my LiveCD. It still didn't work!

Maybe I need to adjust grub's settings?

---

### Post by silentrebel on 2009-04-21
The best program to use for what you are doing is gparted (as you may know). The liveCD should have all the packages you need, but just in case, open a terminal and type the following:

sudo apt-get update
sudo apt-get install gparted ntfsprogs

-Now open gparted (sudo gparted) (make sure you backup anything important you may have on either of your partitions in case anything goes terribly wrong (though this is not normally the case)).
-Select the right hard disk.
-You should see a list of your partitions. It seems that upon installing Ubuntu an extended partition is created in which your filesystem and your swap are created. Right-click on the linux-swap partition and select the swap-off option. This unmounts it so that we may make changes to the extended partition of which the filesystem is a child.
-Now right-click the extended Ubuntu partition (the one that contains the two sub-partitions) in the tree-view and select Resize/Move. Make the changes you want to make. We need to do this first to make room for the Ubuntu filesystem partition within its parent's boundries.
-Now right-click your Ubuntu filesystem partition in the extended partition, select Resize/Move and make the desired changes.
-Now review everything and apply changes. It may take a while......
Good luck
Let me know if you have problems... or if it works...
**Note that moving your partition left can take a very long time (especially if the moved parition is big).  For this operation, the partitioner needs to copy every block of your existing partition to another location on the hard drive...  Better take a nap... **

---

### Post by CatKiller on 2009-04-21
> **Flexico said:**
> [--unallocated--][---ubuntu---][-swap-]

"Partition Editor" won't let me move my ubuntu partition left to fill the unallocated space! I boot from my USB startup drive so I can move the bootable partition, but even though I can resize the "right" side, the "left" side can't be moved. It's as if the empty space isn't there!

Is your Ubuntu partition inside an extended partition? If so, you'll need to resize that first.

---

### Post by Flexico on 2009-04-21
Thanks all! I had to boot from the CD, then "unswap" the swap partition, unmount the Ubuntu partition, then first resize the extended partition, then resize the Ubuntu partition. Wow. But it's all working now! Thanks! ^_^

---

### Post by silentrebel on 2009-04-21
I'm glad it works.  
Why don't you set this thread to *solved* so that others can know that this is a source for help and no longer requires attention.

---

### Post by Flexico on 2009-04-21
Good idea---how do I do that?

---

### Post by silentrebel on 2009-10-09
Above the posts and to the right, there is a drop-down menu named "Thread Tools."  Click on it, then select "Mark this thread as solved."
Tada!

---

