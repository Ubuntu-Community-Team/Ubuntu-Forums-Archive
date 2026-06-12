---
title: "Partitioning Help"
date: 2009-05-22
forum: General Help
---

### Post by Waffle07 on 2009-05-22
Hey everyone,

I just freed up some Hard Drive Space from vista. I want to combine the unallocated space and the ubuntu partition. I tried to do it but for some reason it wont let me extend the ubuntu partition if the the space is before the partition. I attach a picture to show what I'm talking about.

Thanks
-Dave

---

### Post by 73ckn797 on 2009-05-22
If you are wanting the space before the Vista partition then you will have to first resize the Vista Partiton to use the space in front of it. You will then have to resize the Vista to give more space at the end (right side) of the Vista partition. Then you could resize the Linux partition. You may actuall have to completely reformat thew drive to get everything back in its place. I have not had this issue so what I say may not work at all without a complete wipe and reinstall.

---

### Post by scradock on 2009-05-22
Your Ubuntu partition is part of an extended partition. You can't change the size of the Ubuntu partition without resizing the extended partition first. Try using a Windows partitioning program to resize the extended partition.

Another tricky thing is that you can't change sizes of partitions if they are mounted, so it's obviously impossible to change the size of the Ubuntu partition using Gparted running in the Ubuntu partition. That means that BOTH the Ubuntu partition and the swap partition will need to be un-mounted before the extended partition can be re-sized. That's easiest done from Windows, though you can do it from a Ubuntu live-CD (or a rescue CD).

HTH

---

### Post by egalvan on 2009-05-23
> **scradock said:**
> Your Ubuntu partition is part of an extended partition. **You can't change the size of the Ubuntu partition without resizing the extended partition first**. [B]Try using a Windows partitioning program to resize the extended partition.
[/B]
Another tricky thing is that **you can't change sizes of partitions if they are mounted**, so it's obviously impossible to change the size of the Ubuntu partition using Gparted running in the Ubuntu partition. That means that BOTH the Ubuntu partition and the swap partition will need to be un-mounted before the extended partition can be re-sized. That's easiest done from Windows, though you can do it from a Ubuntu live-CD (or a rescue CD).

HTH

Yep, partitions need to be un-mounted to make changes to them...

But you certainly don't need Windows-stuff to do this...

Either use the CD you used to install Ubuntu (as a Live CD)
or download PartedMagic and do the partition changes with that.
(yes, there are other packages that will do this work...
this is my personal favorite, so I recommend it)

[** http://partedmagic.com**]("http://partedmagic.com/")

---

### Post by Waffle07 on 2009-05-23
> **scradock said:**
> Your Ubuntu partition is part of an extended partition. You can't change the size of the Ubuntu partition without resizing the extended partition first. Try using a Windows partitioning program to resize the extended partition.

Another tricky thing is that you can't change sizes of partitions if they are mounted, so it's obviously impossible to change the size of the Ubuntu partition using Gparted running in the Ubuntu partition. That means that BOTH the Ubuntu partition and the swap partition will need to be un-mounted before the extended partition can be re-sized. That's easiest done from Windows, though you can do it from a Ubuntu live-CD (or a rescue CD).

HTH


Thanks.

I still can't get it. I uploaded another picture because I don't think I'm being clear enough. I just want to extend the Ubuntu partition to the left and use up some of the unallocated space.

Also, I did boot from the live CD and tried to extend the partition with no success. For some reason it just wont let me extend it to the left. I can extend it to the right tho = /.

---

### Post by scradock on 2009-05-23
OK, as egalvan says, no need to use Windows - I thought you might be more comfortable with it since you're apparently moving away from Vista and towards Ubuntu.

Boot from the LiveCD, which has Gparted on it, and open up the view you show in your pictures. There are three relevant partitions: - sda2, sda5 and sda6. All of them need to be un-mounted. They may be, but they may get mounted when you boot up - the most likely one is sda6, the swap partition. If any one of these is mounted, you will not be able to do anything to change the sizes as you want. 

If the keys are showing against any of these three in Gparted, right click on the line and choose Unmount, or Swapoff if it's sda6. Make sure there are no keys showing.

Now you should be able to select sda2, the exended partition, and re-size it to the left. Do that - it may take some time. After Gparted reports it has finished, check there are no keys showing.

THEN you should be able to re-size sda5, the Ubuntu partition, to the left.

If that fails, you can wipe out all three (first sda5 and sda6, then sda2) and set them up again in the un-allocated portion of the drive. make sure you don't have any data files in Ubuntu, of course. (You are most likely going to want to re-install Ubuntu in any case, once the partition sizes are right - but you have the LiveCD so that's not a great problem.)

Hope that helps

---

### Post by Sef on 2009-05-23
1) With Vista, you should use its partitioner to shrink the partition.  

2) Windows should be on the first primary partition; otherwise, you may encounter problems.

---

### Post by DeMus on 2009-05-23
> **scradock said:**
> (You are most likely going to want to re-install Ubuntu in any case, once the partition sizes are right - but you have the LiveCD so that's not a great problem.)

Hope that helps


If a re-install is necessary wouldn't it be easier to just delete everything belonging to Linux and have one big unallocated portion of the disk.
Then start re-install and let Ubuntu use this unallocated part. In my opinion this is easier and faster than adjust sizes and then do a re-install after all.

---

### Post by scradock on 2009-05-23
Sef is right - if you must go on using Vista do as much as you can from Vista so that it stays comfortably thinking it's in control.

DeMus is right - just wipe out the Linux partitions,leaving the space unallocated, and let the LiveCD partitioner set it all up for you as a fresh install. 

BUT - half the fun of linux is finding out ways to do things, isn't it?

---

