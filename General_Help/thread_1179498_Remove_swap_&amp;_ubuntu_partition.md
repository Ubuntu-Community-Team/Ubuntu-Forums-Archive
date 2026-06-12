---
title: "Remove swap &amp; ubuntu partition"
date: 2009-06-05
forum: General Help
---

### Post by Yizi on 2009-06-05
Hi,

I installed Ubuntu on my iMac and it just didnt turn to be easy to use as it is in my laptop and now im stock with the partitions, i can't delete them even in disk utility, can anyone help?

---

### Post by MikeTheC on 2009-06-05
What do you mean you can't remove them? Can you be more specific? What error messages do you get?

In Disk Utility, you should be able to click on the storage device itself, click on the Partitions tab, pick some new number of partitions (1, for instance), then click on the "Options" button below and make sure that GUID is chosen, click OK, and tell it to execute the partitioning process.

Well, that'll put you back to a Mac OS X-only configuration, of course. That may or may not be ultimately what you're looking for, I suppose.

However, we still need you to put up some more details before any of us can really help further.

---

### Post by Yizi on 2009-06-05
I found out myself, follow this if you have the same problem:

1. Enter the Ubuntu live CD
2. Open partitioner
3. Located the swap and linux partition
4. Delete!
5. Login to OS X and use disk utility to extend the partition (unlocated space)

Simple!

---

### Post by JCoster on 2009-06-05
If that doesn't work then use the Ubuntu live-CD to delete them using 'Partition Editor' found under System > Administration.

You'll be able to format them to a filesystem compatiable with Mac OSX.

EDIT: Got beaten there!

---

### Post by MikeTheC on 2009-06-05
Well, normally Linux distros all use the MBR partitioning scheme. Apple uses GUID on Intel-based systems, so simply leaving your HDD partitioned using MBR will result in a system you can't boot into Mac OS X from.

---

### Post by Yizi on 2009-06-05
> **JCoster said:**
> If that doesn't work then use the Ubuntu live-CD to delete them using 'Partition Editor' found under System > Administration.

You'll be able to format them to a filesystem compatiable with Mac OSX.

EDIT: Got beaten there!

nah! your good mate, keep up the good work! love ubuntu on my laptop tho

---

### Post by blueridgedog on 2009-06-05
The live CD will mount the swap partition, so before trying to delete it, you will need to turn swap off.

```
swapoff -a
```

---

