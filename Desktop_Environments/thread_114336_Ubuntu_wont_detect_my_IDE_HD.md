---
title: "Ubuntu wont detect my IDE HD"
date: 2006-01-08
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-01-08
I have two SATA disks, and they are both detected just fine by Ubuntu. When I open Gparted, they are both there, and ive also mounted them succesfully.

I have a 200gb IDE disk, which i also want to mount, but ubuntu doesnt seem to find it. *windows finds it just fine, so it is connected right...


any idea on how to go about solving this problem?

---

### Post by deity_me on 2006-01-08
How is it connected?
You might have to partition it and then format it and then mount it

Primary master -> HDA1
Primary slave   -> HDB1
Secondary Master -> HDC1
Secondary Slave -> HDD1

to partition it, run cfdisk /dev/hdx where x is a,b,c,d depending where its placed
but before you do that run df just to make sure /dev/hda1 and /dev/hdb1 are not in used b/c i'm not too sure where linux place sata disks

after you've partitioned run
mkfs -t ext2 -j -m 0 -c /dev/hdx1
makes an ext3 file system with 0% space reserved for the root (i dont find it necessary to leave extra space for the root on storage drives)
the -c option does the LONG format (surface check - my 320GB drive took almost 2 hours yesterday)

if you've done all these - then ignore what i've said as i havent been around the linux world in a few years

---

### Post by stiankarlsen on 2006-01-08
the problem is that ubuntu wont register the disk at all, and therefore not place it under /dev/xxx

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=stiankarlsen]the problem is that ubuntu wont register the disk at all, and therefore not place it under /dev/xxx[/QUOTE]
You might have more luck in the hardware forum if you posted the model of the drive there.  Someone might be familiar with that particular model, as normally, IDE drives just work with the standard drivers.

---

