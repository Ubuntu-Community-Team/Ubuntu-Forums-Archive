---
title: "How to unmount /home partition and extend it ( increase it's size ) ?"
date: 2009-06-04
forum: General Help
---

### Post by ActiveFrost on 2009-06-04
Ok, so .. I've an extended partition, but somehow, media preview ( can't view movie thumbnails, etc. ) does not work !
I want to delete it and extend my /home partition .. how to do that ? gParted will not allow me unmount my /home partition as it's currently in use.

Any help appreciated :)

> Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28232823

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            4509        9733    41969812+   f  W95 Ext'd (LBA)
/dev/sda3            4387        4508      979965   82  Linux swap / Solaris
/dev/sda4            1217        4386    25463025   83  Linux
/dev/sda5            4509        9733    41969781    7  HPFS/NTFS

---

### Post by b0b138 on 2009-06-04
boot from the live cd so it won't be mounted.

---

### Post by ActiveFrost on 2009-06-04
> **b0b138 said:**
> boot from the live cd so it won't be mounted.

I can't do it from a live CD ! I've deleted my extended partition and there's like 40GB unallocated disk space, but - I can't add it to /home ( it simply does not allow me to increase it's size ).
What could be the problem ?

---

### Post by Phreakerr on 2009-06-04
Try googling around for the livecd version of GParted.  That's what helped me.

---

### Post by merlinus on 2009-06-04
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by uupreti on 2009-06-04
> **ActiveFrost said:**
> I can't do it from a live CD ! I've deleted my extended partition and there's like 40GB unallocated disk space, but - I can't add it to /home ( it simply does not allow me to increase it's size ).
What could be the problem ?

In my understanding, if your partition is traditional one then you can't merge other space to already existing partition to make its bigger. For that case you have to make partition using LVM. Once you created a partition using LVM then you can add extra space whenever you want.

If I got your question correctly. :)

---

### Post by merlinus on 2009-06-04
Are you saying that free space cannot be added to an existing partition without using LVM?  And what do you mean by a traditional partition?

---

### Post by merlinus on 2009-06-04
@ ActiveFrost --

If you boot from the live cd and run gparted, what does it show now that you have deleted your extended partition?  Can you post a screenshot?

Or post results of terminal command:

```

sudo fdisk -l

```

---

### Post by uupreti on 2009-06-04
> **merlinus said:**
> Are you saying that free space cannot be added to an existing partition without using LVM?  And what do you mean by a traditional partition?

That was my understanding with linux (redhat/centos/fedora) sytem when I started using it few years back. I have not so much deep experience about ubuntu system and it's feature. I mean traditional partition is just a partition where you simple create mount point, give a size and specifiy one of the listed filesystem ext2, ext2 blah blah blah. Its basic partition in my view.

If my concept is not clear then clearification will be highly appreciated.

---

### Post by merlinus on 2009-06-04
There are three kinds of partitions, primary, extended, and logical.  You cannot have more than four primaries on one hdd, so often it is good to have one at the beginning, and then create an extended using all the rest of the space.

You can have dozens of logical partitions within an extended, so creating, deleting, moving, and resizing is very easy.

Also, it is possible to use a disk partitioning tool such as gparted to copy, move, and/or resize partitions.  They cannot be mounted whilst doing so, and booting from the live cd is preferable for this kind of work.

hth...

---

### Post by uupreti on 2009-06-04
Ok then what's the benefit of using LVM over it?? May be because we can create more than 16 logical partition??

---

### Post by ActiveFrost on 2009-06-04
To everyone who've tried to help me so far - I deleted my extended partition from a Live CD ( gparted ) and tried to increase my home partitions size, but .. once I click Move/Resize, there's no chance I could increase it's size ( arrow is disabled and I can't type bigger number than the default one ).
Maybe it's due to the fact that my home partition is set to "Primary" ?

Anyway, I made a new ext3 partition, so .. I don't need to resize my home partition anymore ! Though, would be nice if someone could find a solution to this problem .. could be helpful for others ( not only for me ) :)

---

### Post by merlinus on 2009-06-04
If you booted from the live cd, then /home was not mounted. But if the new space was not right next to it, then it is not possible to resize into it. 

I do not think it being a primary partition had anything to do with it, but who knows?

Without a screenshot of the situation, it is hard to guess exactly what was happening.  But it seems as though you found a workaround.

---

### Post by merlinus on 2009-06-04
[SIZE=3]@[COLOR=Black] uupreti
[SIZE=2][]("http://ubuntuforums.org/member.php?u=830486") 
I do not know anything about LVM, but iirc you can have at least 50 logical partitions in an extended one.[/SIZE]
[/COLOR][/SIZE]

---

