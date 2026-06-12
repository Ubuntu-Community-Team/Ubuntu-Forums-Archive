---
title: "Extending Linux Partition"
date: 2009-04-26
forum: General Help
---

### Post by acidboot3r on 2009-04-26
I'm trying to extend my linux partition using GParted, but I can't seem to grow it into the unallocated space provided. 

Here is a screenshot of what I'm trying to do:


[IMG]http://i40.tinypic.com/2d84yzq.png[/IMG]

To put it simply, I'm trying to extend /dev/sda5 by letting it take up space from the unallocated partitions and possibly /dev/sda3. Every time I try to extend however, it will show now available space to be extended. I've tried booting into GParted while the linux partition isn't mounted and it still gives me the same result. 

Also, it gives me the same result if I tried to extend my Vista partition (/dev/sda1). Only /dev/sda3 is extendible.

---

### Post by drs305 on 2009-04-26
sda5 lies within an extended partition (sda2) and can only take or give space from within the light blue bordered area (sda2). So you would first have to expand sda2 to incorporate more space, and then once it is *inside* sda2 you can expand sda5.

Back up critical data before doing any partitioning.

If you want to take some more space from sda3:
Decrease the size of sda3.
Expand sda2 to include the free/gray space to it's left and right.
Move the swap to one end or the other of sda2.
Increase the size of sda5.

Hint: To select the extended partition (sda2) you have to select it by clicking on it in the lower panel, not on the graphic at the top.

You will have to do this from outside your normal system as you cannot do this with mounted systems. Boot from the LiveCD or use a third-party CD such as the GParted or SystemRescueCD.

---

### Post by acidboot3r on 2009-04-26
OK I expanded the sda2 partition and now it has an extra 6 GB or so of free space.

Now all I want to do is expand sda5, but I don't understand your instructions? I have to shrink sda5? which would take ages, and then move around the linux swap partition? Sorry but I'm not an expert at these sort of things.

As you can see, sda2 has grown in size:

[IMG]http://i43.tinypic.com/30m08sk.png[/IMG]

---

### Post by drs305 on 2009-04-26
Backup important data first.

From the LiveCD, expand sda2 to the left so there is no more gray space on the left.
Move sda5 so it is at the far left of sda2.
(Optionally, you could also move sda3 to the far right at this point and expand sda2 to the right as well, to give you even more space in sda2).
Move sda6 (swap) so it is at the far right of sda2.
Finally, expand sda5 to incorporate all the gray space within sda2.

Here is a good link on partitioning:
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by acidboot3r on 2009-04-26
Ok thanks for all your help, I'm going to try moving everything as soon as I put Ubuntu on my usbstick.

---

### Post by acidboot3r on 2009-04-26
Ok I'm in the Ubuntu Live CD and I'm using Gparted from there. The sda2 partition is locked because it says at least one logical partition is mounted? 

Anyways, I can't move the sda5 partition around becase all it shows is some sort of white space?:

[IMG]http://i41.tinypic.com/f1xwrk.png[/IMG]

The linux swap partition is locked too, so I can't move it.

---

### Post by drs305 on 2009-04-26
Are you doing this from the livecd? As mentioned earlier, the operation won't work on mounted partitions. Since the ones you are trying to move (/, swap) are system partitions, they would be mounted if you booted normally and the / partition can't be unmounted.

If you booted from the livecd, you need to umount the partitions you are going to work with and any partition. So right click sda5 and select "unmount". Swap is a little different, you select "swapoff".

In your latest pic, you haven't expanded **sda**2 yet so you can't expand any partition inside it. Once you have done that, to expand a partition, you can put your mouse on the edge of the partition and drag it to the edge.

---

### Post by acidboot3r on 2009-04-26
I unmounted the swap partition. sda5 is unmounted. I just can't unmount the sda2 extended partition. Will that be a problem?

And what ext2 are you talking about?

Oh wait nevermind, the sda2 is free! I didn't check ^_^

---

### Post by acidboot3r on 2009-04-26
Ok nevermind, I manage to extend the sda5 partition fine!

---

