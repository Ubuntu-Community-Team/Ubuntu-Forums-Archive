---
title: "Partition Layout for Dual Linux Box"
date: 2006-09-21
forum: Desktop Environments
---

### Post by lazywanker on 2006-09-21
I want to setup my box to multi boot 2 distros on one hard disk and Windows on the second.  

For the most part one distro will stay stable and the other will be for messing about.  However since I often manage to break my 'stable' install I want to keep my data on a completely seperate partition (which can also be read by Windows). I'm thinking ext3 since there's a Windows driver for that. 

Also I think sharing the swap would also be fine.  But what about the rest  (./ /boot /home etc.)?  Also does hibernation in linux use the swap partition or something else?

What would be the best partition layout to use?

---

### Post by aysiu on 2006-09-21
There does not need to be a separate /boot partition. And if you have a separate partition for data, you don't need a separate /home partition either.

Yes, you can share swap between two distros, and you can read/write Ext3 from Windows using [http://www.fs-driver.org](http://www.fs-driver.org)

For more on partitioning...
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by lazywanker on 2006-09-21
Thanks for the answer and the link.

I think I'll end up going with the following :

/           <root for distro 1
/           <root for distro 2
/data       <shared data
/swap1      <swap for distro 1
/swap2      <swap for distro 2

The two swaps are because sometimes hibernation can be very useful.  

Hmm... I could also put all 3 OSes on one drive and use another drive for all my data.  Any thoughts on which is the better approach?

---

