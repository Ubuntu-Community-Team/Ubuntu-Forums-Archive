---
title: "removing partitions to re-install..."
date: 2009-04-03
forum: General Help
---

### Post by Xender1 on 2009-04-03
I am going to reinstall ubuntu, but first I want to try and clean up my partitions. Currently I have /dev/sda1 which is 142gb and is where ubuntu is currently installed. But I also have a second partitions that is /dev/sda2 and it is extended, and includes a /dev/sda5 which is the linux-swap (that was there from a previous dual boot setup). is there anyway to clear out the extended partition so it is all /dev/sda1 and so ubuntu takes up all possible space? im looking at it in gparted now and cannot delete the extended or linux swap partition.

---

### Post by taurus on 2009-04-03
You first need to unmount the swap partition before you can delete it.  Highlight /dev/sda5 and click the right button and then swapoff.  Now, you should be able to /dev/sda5.  Then, delete /dev/sda2 and expand /dev/sda1 to take up the unallocated space.

---

### Post by coffeecat on 2009-04-03
Whoah, hang on a moment! You shouldn't run Linux from just one partition. Unlike Windows, Linux uses a dedicated swap partition, so to have your root partition as sda1, and swap in logical sda5 is perfectly OK, so long as there isn't unallocated space you want to recover.

I'm presuming there is, so once you've removed sda2/5 and resized sda1, make sure you create a swap partition.

---

### Post by Xender1 on 2009-04-03
after resizing, would doing a reinstall of ubuntu from the liveCD create that swap partition automatically?

---

### Post by taurus on 2009-04-03
It depends on what option you pick when you get to the partition screen, Step 4 of 7.  If you have only one partition that takes up the whole disk space, then you can tell the installer to use the whole disk and it will create one large partition for / (root filesystem) and a smaller one for swap.  But if you already have / and swap, then you would pick the Manual option and tell the installer the mount the first one (or the large partition) to / and the smaller partition to swap. 

 In fact, you can even have more one two partitions if you'd like:  /, /home, & swap.

---

