---
title: "How to Read/Write on Mac Formatted External Hard Drive in Ubuntu"
date: 2009-06-12
forum: General Help
---

### Post by amerikanYippie on 2009-06-12
Hi, I'm somewhat new to Linux OS's and have a question regarding external hard drives.
 
My main computer is a MacBook Pro, running OS X 10.5.1. As I understand it, this means that the Maxtor OneTouch 4 (250GB, I think) External Hard Drive I use with my Mac is HFS+ partitioned. Correct?

I want to be able to read and write to this external HD on my Dell Inspiron 600m, which is now running Ubuntu 9.04 (Jaunty Jackalope), without losing any of the files that are on it now, and without losing the ability to use it on my Mac.

I've read a few solutions using GParted, but those were mostly for older versions of Ubuntu, and somewhere else I read that 9.04 can read HFS+. Should I just be able to plug it in and use it in either computer? I really can't lose any of the files on it, so I don't want to do anything I'm not 100% sure will work.

Thanks!

---

### Post by DGortze380 on 2009-06-12
> **amerikanYippie said:**
> 
My main computer is a MacBook Pro, running OS X 10.5.1. As I understand it, this means that the Maxtor OneTouch 4 (250GB, I think) External Hard Drive I use with my Mac is HFS+ partitioned. Correct?


Not necessarily. Most external drive come formatted NTFS (or FAT32), unless you or an install utility reformatted to HFS+, it's actually quite unlikely that it's HFS+.

I believe disk utility will tell you.

> **amerikanYippie said:**
> 
I want to be able to read and write to this external HD on my Dell Inspiron 600m, which is now running Ubuntu 9.04 (Jaunty Jackalope), without losing any of the files that are on it now, and without losing the ability to use it on my Mac.


You need to disable journaling for an HFS+ drive via disk utility in OS X in order to write to it in Linux.

Your other option is to use NTFS, which has great support in both Linux and OS X. ntfs3g is the package/drive you need on both machines in order to do this. Should be installed by default in Ubuntu.

---

### Post by amerikanYippie on 2009-06-12
> **DGortze380 said:**
> Not necessarily. Most external drive come formatted NTFS (or FAT32), unless you or an install utility reformatted to HFS+, it's actually quite unlikely that it's HFS+.

I believe disk utility will tell you.



You need to disable journaling for an HFS+ drive via disk utility in OS X in order to write to it in Linux.

Your other option is to use NTFS, which has great support in both Linux and OS X. ntfs3g is the package/drive you need on both machines in order to do this. Should be installed by default in Ubuntu.

My Mac is actually in the shop right now, but I just went ahead and plugged the HD into my PC, and I'm able to read all the files except for my music folder, for some reason.  It has an X in a box above the icon. 

The HD is HFS+ formatted (or so says the File Systems tab in System Manager).  I'm also unable to write to it.  Is there any way to change the permissions outside of OS X?  Or must I wait until my computer comes back from the repair shop?

Thanks.

---

### Post by albinootje on 2009-06-12
> **amerikanYippie said:**
>  The HD is HFS+ formatted (or so says the File Systems tab in System Manager).

It is mounted read-only. Like someone else already mentioned you need to disable the journal. 

Perhaps you have friends with Apple computers which you can use for a minute to disable that journal. If not, wait till your Apple machine is back.

---

### Post by DGortze380 on 2009-06-12
> **amerikanYippie said:**
> My Mac is actually in the shop right now, but I just went ahead and plugged the HD into my PC, and I'm able to read all the files except for my music folder, for some reason.  It has an X in a box above the icon. 

The HD is HFS+ formatted (or so says the File Systems tab in System Manager).  I'm also unable to write to it.  Is there any way to change the permissions outside of OS X?  Or must I wait until my computer comes back from the repair shop?

Thanks.

You need OS X to safely disable journaling to the best of my knowledge.

---

