---
title: "how can I Expand the size of /home after install"
date: 2010-09-24
forum: Desktop Environments
---

### Post by kalel17 on 2010-09-24
Hi this is my first post on the forums but I have been using ubuntu for about a year now. Since then one main thing have evaded me: how to increase the size of /home without reinstalling the OS. I tried to change the size from the default 200mb once while installing and it ended up messing up my hard drive, so I decided not to do it this time around because I have important stuffs on it.

Is there a way to map /home unto another block of free space?

Thanks in advance for your help

---

### Post by DonEsteban on 2010-09-25
I'm not aware of any out-of-the box way to do what you want. You cannot just assign free space somewhere on your disk to an existing partition (or mount point). If you have free space directly before or after your existing home partition on the same hard drive, partition managers like GParted, KDE Partition Manager, or Commercial tools like Partition Expert can probably resize it. If the free space is on the same drive, but not directly next to your existing partition, it *might* still be possible. If it's not on the same drive, forget it: You either have to completely move the data from the old partition to the new disk or mount the new disk somewhere else.

Before you try anything like this, do a full backup! In fact, even if you don't want to do anything like this, do a full backup.

---

### Post by Rinzwind on 2010-09-25
> **kalel17 said:**
> Hi this is my first post on the forums but I have been using ubuntu for about a year now. Since then one main thing have evaded me: how to increase the size of /home without reinstalling the OS. I tried to change the size from the default 200mb once while installing and it ended up messing up my hard drive, so I decided not to do it this time around because I have important stuffs on it.

Is there a way to map /home unto another block of free space?

Thanks in advance for your help

symlink


I have a 5 Gb Home and remove ~/Desktop after installing a new Ubuntu and do a
ln -s /home/rinzwind/Desktop /discworld/Desktop


All my icons and movie-files I want directly on my desktop are inside /discworld/Desktop and /discworld/ also holds all other files.

If you want you can keep /home the size you have and store all files outside your OS directories (on an external disc if need be) and just do a symlink to that location.

---

### Post by kalel17 on 2010-09-25
Thanks for the replies, how do I go about doing this?

---

### Post by nagaprathyush on 2010-09-25
I suppose, Rinzwind has already given the solution in his previous reply....Just, open a terminal(applications->accessories->terminal) and type
ln -s /path/to/your/desired/partition /home

I created a symbolic link(similar to a shortcut) with his reply. What I did was....

ln -s /media/STUFF ~/Desktop

That's all.......

---

### Post by kalel17 on 2010-09-25
I did:

sudo ln -s/media /home

to link it with the remainder of my hard drive partition but my downloads are still going to /home/idu/Documents...

---

### Post by nagaprathyush on 2010-09-25
hey, I think /media is just a mount point for your hard disk partition or media that you plugin(say a usb or thumbdrive). So, why not try create a link to /media/some_partition rather than /media and ask your browser or p2p client to download to /media/some_partition. 
Come to think of it ... why were you trying to create a link so that clicking on your home directory takes you to /media ?....I am afraid, that might cause some unexpected/expected issues,instead create another symbolic link/shortcut.

---

### Post by kalel17 on 2010-09-25
> **nagaprathyush said:**
> hey, I think /media is just a mount point for your hard disk partition or media that you plugin(say a usb or thumbdrive). So, why not try create a link to /media/some_partition rather than /media and ask your browser or p2p client to download to /media/some_partition. :popcorn:

I tried doing it with /media/08C83853C83840EC which links to a partition of my hard drive but I am having the same problem. The download is not the problem, what really is the problem is that installing softwares seems to eat into the space, and I only have around 200mb in /home

---

### Post by nagaprathyush on 2010-09-26
Ohh, I am not sure if you can mount your home directory in some other partition. Had it been some other OS, it would have been impossible...but am not sure about linux.:( 

Bump this thread up until some pro steps ahead and makes things clear ......

---

### Post by perspectoff on 2010-09-26
If you have any free space on your hard drive, you can move existing partitions left or right until the free space is adjacent to the partition with your /home directory. Then just expand the size of the partition with /home in it.

This can all be done with GParted and is pretty intuitive from the GUI.

If you don't have free space, you will have to shrink an existing partition to free up some space, then move the partitions as above, and then enlarge the /home partition.

I wouldn't recommend changing the size of any Windows Vista/7 partitions (NTFS) with GParted, though.

It is not particularly difficult to add a second hard drive, if you really have mountains of data, create a new /home partition on it, and then edit the fstab configuration file to reflect that partition as your permanently mounted /home partition. You would then just copy your files from the previous partition to that one, using a file manager (Nautilus, for example) or something. (Heck you could even copy them first to a USB or CD, even, and then copy them over).

---

### Post by nagaprathyush on 2010-09-26
@perspectoff
That was really helpful and now, I began to think if it could be possible to just copy paste the home folder to an external hard disk or some other partition and edit the fstab file accordingly.... Is that what you meant ? cheers!:)

---

