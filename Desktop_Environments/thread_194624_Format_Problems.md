---
title: "Format Problems"
date: 2006-06-11
forum: Desktop Environments
---

### Post by dareofficer on 2006-06-11
I can't format part of my hard drive.  It says freespace.  I need some help.  I have a picture to look at.

---

### Post by bruce89 on 2006-06-11
It is what it says - you can't have more than 4 primary partitions.  Why do you have 2 linux-swaps anyway?

---

### Post by dareofficer on 2006-06-11
I have Suse, and Ubuntu.  I need to use the open space for swap area.  Is this possible?

---

### Post by dareofficer on 2006-06-11
Is there anyway that I can use this space at all?

---

### Post by bulldog on 2006-06-12
By my knowings you can use one swapfile for all of your Linux distro's in the first place.
Correct me if I'm wrong but a swap is a primary as far as I know so your primary's are used.

But you have a logical drive allready,isn't it possible to create a logical in the extended partition?

---

### Post by scxtt on 2006-06-12
[QUOTE=bulldog]By my knowings you can use one swapfile for all of your Linux distro's in the first place.

<snip>
[/QUOTE]yeah, this is true ... i used to use 1 swap for 3 or 4 distros ... right now i'm using 1 swap for 5.10 (/dev/sda) and 6.06 (/dev/sdb) ...

---

### Post by anaconda on 2006-06-12
Swap doesn't have to be on a primary partition. I have had a logical swap partition, and it worked fine.

And you can also use a swap file, which is in your linux-partition, swap doesn't need its own partition at all, it can be just a file....

---

### Post by anaconda on 2006-06-12
As you (propably) know.. you can have maximum of 4 primary partitions, or 0-3 primary partitions and an extended partition. Extended partition can be divided to as many logical drives as you want..  Logical drives are wery similar than primary partitions. Biggest difference is that you cant? install windows to a logical drive...

Anyway. I suggest that you (backup and) delete your existing logical partitions and the extended partition, and then create new (big) extended partition, which covers all the available space. Then you can make as many logical partitions as you want. ANd you could use the whole hard-disk..

From the picture:
backup hda5  (2,9GB)
delete hda6, hda5, and hda4
then create extended partition using all the remaining space. And then make logical partitions inside the extended partition....

---

### Post by dareofficer on 2006-06-13
I'am new to Linux.  

1. How do I back up the systems?  I have both Ubuntu, and Suse 10.1.
2. How do I format the hard drive after, and then restore them?

I have a external Hard drive, that is 200 GB.  Can I use that to back up?

Thanks for you help!

---

### Post by anaconda on 2006-06-13
The only partition, which you should backup is hda5, which contains 2,9GB of data. And from the picture it looks like you have plenty of free space in both hda1 and hda2 they both have more than 40GB free space. 

Just boot your machine normally, and then copy everything from hda5 to somewhere else. propably hda1 or hda2. (which have lots of free space.) 

You dont need your external had-drive now, because you aren't going to delete any of the paritions hda1, hda2 or hda3.

Just the small hda5.(and you second swap, and the extended partition) Which can be copied to hda1, or hda2.. or if you want to your external hard-drive.

But you dont really have to delete any partitions, you just need to stretch your extended partition to cover the unallocated space in addition to what it covers already. I know it can be done. (not the how part though) And then you can make new logical drives to the larger extended drive. So you would get the extra 70GB to use as you wish.

I just think, that it usually is better to delete partition and create a new different sized partition than to resize existing partitions... (atleast when it is easy to do so, like in your case, where you need to backup only 2,9GB) Maybe it is old info, but eg. in fat-partitions the block-size stayed the same (=bigger) after resizing.. so it was better to create new partitions than resizing old.. IF possible..I suppose it is similar with the newer fs:s too..

Remember, if you delete your swap partition, you may have to point the other linux to use the first swap...

---

