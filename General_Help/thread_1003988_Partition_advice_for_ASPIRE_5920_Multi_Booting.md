---
title: "Partition advice for ASPIRE 5920 Multi Booting"
date: 2008-12-06
forum: General Help
---

### Post by kenji.nanashi on 2008-12-06
Hi, I've recently bought an ACER ASPIRE 5920 with Vista preloaded. Liked it, but I remembered using Ubuntu a while back and liking it. So I popped my 8.10 CD in the drive and installed via WUBI on my D partition, having 4 partitions on my HD and not wanting to mess up.

The HD (~250 GB) has four partitions:
#1 is just over 10 gigs, hidden in windows, where the recovery software and images are
#2 is my C drive
#3 is my D drive, labeled "DATA"
#4 is also a hidden partition, don't really know what for

I've been using ubuntu 90% of the time, switching to vista only for some games, and would like to upgrade my system, getting rid of the hidden partitions, using a dedicated one for ubuntu and having a different partitions for other distros (no offense to ubuntu, I'm just curious).

In a perfect world, I'd need to:

1) Get rid of the 2 Hidden partitions (I believe that as long as I've burned the recovery DVDs, should I need to restore to factory defaults, these should suffice, please correct me if I'm wrong)
2) Move Windows to the front of the drive on a primary partition (50 GB as I use this for gaming and audio production)
3) Move my WUBI to a dedicated partition (extreme measure would be to reinstall from scratch, but I'd much rather not)
4) Have a dedicated Ubuntustudio partition for when I need to work
4) Have a series of Logical/Extended partitions where I can install distros for testing, from what I understand I should be able to have more partitions this way, where I can easily install/remove different distros
5)Have a shared partition where I can keep my shared files I need to access from Windows, Ubuntu and my testing distros.

I _DO_ realize it's a complicated issue, and don't know if I can ever achieve it, but I sure would like to give it a try.

PS I have some files on an external USB HDD in NTFS, never had problems accessing these in Ubuntu, I figure this should apply in my "ideal world" too???

Does anyone have some advice on what the best procedure to follow would be??

Many thanks

---

### Post by kenji.nanashi on 2008-12-07
really, anyone????

---

### Post by Idefix82 on 2008-12-07
First a word of warning: you can lose data while moving partitions, so backup your valuable data onto the external hard drive first.

You steps 1. and 2. can be done with GParted. You have to boot from the Live CD and there you can delete partitions, move partitions and resize them. Make sure you first defragment the Windows partition several times.

For step 3. I believe there are guides out there for how to move a WUBI installation onto a dedicated partition. I have never worked with WUBI and I would probably go for a fresh install.

Any additional partitions can be created when you install a new OS. You don't need to create extended partitions now, since you will have three partitions so you will always be able to add an extended one.
Hope this helps.

---

### Post by kenji.nanashi on 2008-12-07
All the important data has already been moved, bad experiences tought me that (all work projects are on an external HD for portability issues).
So basically I should uninstall my WUBI and free up the space, reboot and use my livecd to move windows to the beginning of the disk, erasing the other partitions to create my future linux space, correct??
Will this not cause problems with windows booting, having moved it from the second to the first partition? Or will installing GRUB sort that out?

Will give it a try and let you know what happens, hoping it all goes well..

---

### Post by Idefix82 on 2008-12-07
Yes, that's what I would do.
It's quite possible that Windows won't boot after that but I would imagine that installing GRUB should sort this out.

---

### Post by caljohnsmith on 2008-12-07
> **kenji.nanashi said:**
> All the important data has already been moved, bad experiences tought me that (all work projects are on an external HD for portability issues).
So basically I should uninstall my WUBI and free up the space, reboot and use my livecd to move windows to the beginning of the disk, erasing the other partitions to create my future linux space, correct??
Will this not cause problems with windows booting, having moved it from the second to the first partition? Or will installing GRUB sort that out?

Will give it a try and let you know what happens, hoping it all goes well..
I would definitely not recommend moving the Windows partition, as that will for sure make it unbootable unless you go through alot of hassle to fix it afterwards; I'm not sure it can even be reliably fixed, because I only know a friend who was able to actually do it once.

I think a better plan might be to just convert that first partition into a data storage partition. Also, you can try and use "[LVPM]("http://lubi.sourceforge.net/lvpm.html")" to transfer your Wubi install to a dedicated partition. If you are sure you don't need the last partition on your HDD, you could delete it and create an extended partition in its place. Then you can create all the logical partitions you might want inside that extended partition. And if you need more room, you could resize the data "D" partition to make space. 

How about first booting your Live CD, open a terminal (Applications > Accessories > Terminal), and post:
```
sudo fdisk -lu
```
And assuming the last partition is "sda4", then do:
```
sudo mount /dev/sda4 /mnt
ls -l /mnt
```
And please post the output; note that "-l" is a lowercase L, not a one. That way we can see what exactly is on your sda4 partition.

---

