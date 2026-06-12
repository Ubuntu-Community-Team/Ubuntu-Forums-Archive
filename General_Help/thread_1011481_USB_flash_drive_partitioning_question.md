---
title: "USB flash drive partitioning question"
date: 2008-12-14
forum: General Help
---

### Post by ukch on 2008-12-14
Hi,

I have a rather specific question regarding partitioning of my USB flash drive. Basically, it seems that every time I plug my flash drive into a Windows machine (other people's, of course!) it gets infected with some virus or other. Since these viruses don't affect Linux, they are not picked up when I use my flash drive on my own Ubuntu machine, and can sit dormant for weeks or months before I plug my flash drive into someone else's computer, at which point they are either detected by the virus scanner or go on to infect that person's computer without my knowledge. Now, obviously I don't want to go around unintentionally infecting people's computers and losing friends in the process! Today, I had a (seemingly) brilliant idea of how to fix the problem. Here is my idea:

* Split the flash drive into two partitions, one very small (1-2MB) FAT partition and one other partition that is unreadable by Windows (probably Ext2 or other Linux).

* Put some kind of Windows program to access the second partition on the first partition, then make the first partition read-only.

In this way, no viruses will be able to infect the flash drive as the first partition will be read-only and the second partition will only be visible to this particular program. I have done a bit of research today and come up with two questions:

* Is it even possible to have a read-only FAT partition? Is it likely that any read-only properties I put on the partition will just be overridden by any virus that wants to infect me?

* Does such an 'Ext2 on Windows' program exist? It needs to be able to read/write to the drive, while being able to be run off a flash disk. I have done some research and found many of these 'driver' programs that add Ext2 read/write capability to Windows Explorer - these are not suitable for my needs, as if Windows can see my disk, then so can any virus.

Does anyone have any ideas? Answers to my questions (either positive or negative) would be appreciated, or of course if you think I'm going about the whole thing the wrong way and have a better idea, tell me. Obviously I know the best solution is to only use my flash drive in a computer that I know is clean, but that's just not practical for me, as I use my drive in loads of different computers belonging to different people (some more careful than others).

---

### Post by lenswipe on 2008-12-14
perhaps downloading a virus scanner to ubuntu would be a good idea(not to protect ubuntu, but to remove viruses from the pendrive that could infect windows machines)

-L

---

### Post by ukch on 2008-12-14
OK. Any suggestions? And would they be able to detect Windows viruses?

---

### Post by sedawk on 2008-12-14
1) There are USB-sticks with a write-protect switch. Haven't seen
   any for a long time (since sticks got bigger then 128 MB).

2) I'm not aware of any trick to make a partition fully read only.
   You can make directories or files read only, but when the
   virus has "root access" that will not help.

3) Like you said, any file system that is accessible by the OS
   is vulernable to the virus, e.g. crypted filesystems.
   So you would need a special "container" and a software layer
   accessing that container without integrating the container
   into the OS - e.g. only some simply upload/download feature.
   But still you might upload/download infected files!

4) Like said above, with clamav there is a virus scanner for Linux.

---

