---
title: "Resizing Paritions Using GParted"
date: 2009-01-18
forum: General Help
---

### Post by setsanto on 2009-01-18
Hi,

I am currently trying to give my windows partition on my hard disk more room and my ubuntu one less.  I currently have this:

[IMG]http://img523.imageshack.us/img523/2849/onesu7.png[/IMG]

I want this:

[IMG]http://img297.imageshack.us/img297/2136/screenshotsd6.png[/IMG]
with the unallocated space being NTFS.

However, GParted tells me I can have no more than 4 partitions.  Is there any way of just adding the unallocated space to my existing NTFS partition without having to wipe it?

~Setsanto

---

### Post by voxel on 2009-01-18
I believe GParted is referring to no more than 4 **primary** partitions.
You can however create as many logical partitions as you want.
It looks like you've already created a logical partition /dev/sda4 (the **extended** one)
The extended partition acts as a container for any number of logical partitions.
I'm not sure if GParted is able to move ntfs partitions, but you probably want to create your new NTFS partition as a logical one. OR, as you said... add the space to the NTFS partition, but that would require moving them.
Hope that helps

---

### Post by theWrkncacnter on 2009-01-18
Your windows partiton is /dev/sda3 right?
What you can do is shrink sda1, move your boot partition and your windows partition as far left as they'll go (if possible -- I think gparted can move ntfs partitions) and then expand your windows partition.
This could take longer than an hour to do though, so be prepared.

---

### Post by setsanto on 2009-01-18
thanks wrank!  it works perfectly.  I can't believe I didn't think of that :P.

~Setsanto

---

### Post by virtuallinux on 2009-01-19
You should probably defragment your windows partition immediately after resizing, as resizing can leave your files rather fragmented, at least in my experience.

---

