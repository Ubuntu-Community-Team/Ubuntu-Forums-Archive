---
title: "Dell Dimension with Vista - partitions"
date: 2011-04-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eastexsteve on 2011-04-01
I once did a Wubi install of 10.04 on my Dell desktop.  In looking at the partitions, I seem to have four of them.  A Dell utilities partion, Drive C;, Drive D:; and a small partition that Ubuntu disk manager calls a container for logical partitions.  Did Vista put this on the drive, or did Ubuntu put this on the drive?  Can I get rid of it if I'm not running Ubuntu on this machine anymore?

---

### Post by bcbc on 2011-04-01
When you install Ubuntu with Wubi, it does not create partitions.  So whatever created that, it was not Wubi.

---

### Post by eastexsteve on 2011-04-02
> **bcbc said:**
> When you install Ubuntu with Wubi, it does not create partitions.  So whatever created that, it was not Wubi.

Well, I've got windows people telling me that Vista didn't put it on their, either.  I don't believe in govt conspiracies, so either Vista or Ubuntu created that logical partition.  Hopefully, someone can give me an answer soon.

I looks like some kind of swap partition that contains data.  But, I can't tell anything else about it.

---

### Post by bcbc on 2011-04-02
> **eastexsteve said:**
> Well, I've got windows people telling me that Vista didn't put it on their, either.  I don't believe in govt conspiracies, so either Vista or Ubuntu created that logical partition.  Hopefully, someone can give me an answer soon.

I looks like some kind of swap partition that contains data.  But, I can't tell anything else about it.

I agree with the 'Windows people'. Vista doesn't modify partitions (through normal use following the installation). Neither does Ubuntu.

Wubi does not modify or create any partitions either through normal use or through the installation. This is the whole point of Wubi: to try Ubuntu in a realistic way, but without partitioning. 

If you installed Ubuntu normally (not with Wubi) then yes, it would definitely have modified your partitions to make room for Ubuntu. 

If you still have an Ubuntu CD lying around, boot from it, select "Try it" (try without installing) and drop to a terminal and run:
```
sudo blkid
``` 
and 
```
sudo fdisk -l
```

That should provide some information about what's going on. If you don't have an Ubuntu disk, post a screenshot of the Windows disk manager.

---

### Post by eastexsteve on 2011-04-02
Ah, many thanks to you.  The "sudo blkid" command says that this is a swap partition.  The "sudo fdisk -l" command identifies this as a: "LINUX SWAP / SOLARIS" partition.

Very good.  Now I can kill it, and merge it with some other blank space and install 10.10-64 bit on this machine.  As it was, I couldn't create any more partitions.  I was already at my limit of four.

Thanks,

Steve

---

