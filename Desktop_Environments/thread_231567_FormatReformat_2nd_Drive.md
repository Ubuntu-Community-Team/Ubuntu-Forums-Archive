---
title: "Format/Reformat 2nd Drive"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Dr.Ph0bius on 2006-08-07
Since this is my first post, a little about me real quick...

My home network consists of 2 windows pc's a pc with 2000 Server, 2 macs, a mac notebook and a pc notebook with a bit over 1 terrabyte of storage. Most of it is things Ive rebuilt and scraped together over the years for use as file servers, web servers, a dedicated P2P machine, a gaming machine and casual use machine.

At one point I installed SUSE, but at that point I wasnt ready to give it the time needed to really adjust. Ive jumped into Ubuntu full force! No dual booting, I wiped the drive clean of windows for a fresh start with this distro.

The install went great, all the updates are applied, everything is running excellent! So now for the question:

I have a second drive (150g, ide) attached. It is currently formatted NTFS, and I would like to reformat it to use as a storage drive for this machine, which I hope to have become my primary desktop. 
Ive tried SUDO to gain read/write control, and Im having no luck with it, I would like to reformat to a Linux friendly format. 

I also plugged in an external drive (probably NTFS, I dont recall right now) and could also not manage to get read/write permission. Is this an issue with it being NTFS? I would like to tranfer data off of the externals, reformat them to FAT and move the data back to them so that every machine can use them (DAMN YOU NTFS!)

I did a few searches, but none of the results were quite what I needed. Is there a way to reformat with the install disk without going through a whole install?

Any help would be great! If all goes according to plan, I'll make the other windows machine Ubuntu, and then when Im feeling confident I'll set the server up too.

Thanks!

---

### Post by Ramses de Norre on 2006-08-07
```
sudo aptitude update && sudo aptitude install gparted
``` will install gparted, a partition editor which will allow you to reformat the drive in ext3.

To read the drive you'll need to mount it first, do sudo mkdir /media/ntfs to create a mountpoint and then do this to mount it: ```
sudo mount /dev/hdb1 -t ntfs -o nls=utf8,umask=0222 /media/ntfs/
```
Replace /dev/hdb1 with the correct device node, ide drives start with hd followed by a letter for the device order (a=prim master, b=prim slave, c=prim master ...) and a number for the partition (starting from 1)

Now the contents of the drive will be in /media/ntfs and you'll have read access, it is currently still impossible to safely write to ntfs without compilling new drivers from source.

---

### Post by Dr.Ph0bius on 2006-08-07
Thanks a bunch! 
I'm getting rid of the NTFS formatting altogehter. Since I'll eventually be fully Linix/Mac, NTFS can pretty much kiss my *** (to put it mildy)!

I have to say that I really appreciate the Ubuntu community. I had some bad experiences with the support groups when I gave SUSE a shot, and that kind of made me shy away from getting into it, but you guys (girls) here are great... If this all goes well (which I think it is going to) I'll be switching my wifes PC over, and my brother will be next (before the windows WGA puts him out of business).

Thanks for the reply!!!

---

