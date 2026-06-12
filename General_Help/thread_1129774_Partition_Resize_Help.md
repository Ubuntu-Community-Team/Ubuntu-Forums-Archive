---
title: "Partition Resize Help"
date: 2009-04-19
forum: General Help
---

### Post by JordanMaster22 on 2009-04-19
I am in my Live CD and I just resized my Windows partition (ntfs) down a couple Gb so my Linux partition could hold more data.  But it won't let me increase my Linux partition (ext3) even though there is a couple more Gb left.  What gives?  Please fix, fast.

When I removed some space from Windows it created an 'unallocated' partition.  Do I have something to do with this?

---

### Post by DeMus on 2009-04-19
> **JordanMaster22 said:**
> I am in my Live CD and I just resized my Windows partition (ntfs) down a couple Gb so my Linux partition could hold more data.  But it won't let me increase my Linux partition (ext3) even though there is a couple more Gb left.  What gives?  Please fix, fast.

When I removed some space from Windows it created an 'unallocated' partition.  Do I have something to do with this?

Please post a screendump of Gparted so we can see how the separate partiitons are organized.

---

### Post by -kg- on 2009-04-19
As DeMus said, we will need a screenshot of your GPartEd screen to tell.

What it sounds like to me is that you have your ext3 and swap partitions contained within an Extended Partition while your Windows partition is a Primary partition.  If so, then when you resized your Windows partition you created free space in Primary space.

What you likely need to do is extend your Extended partition into the free space.  Then you will be able to extend your ext3 partition (which would be a Logical partition if it is contained in an Extended partition) into the space within your Extended partition.

A good guide on partitioning operations is:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

I suggest reading the information on these pages.

---

### Post by JordanMaster22 on 2009-04-20
I figured it out.

---

