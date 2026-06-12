---
title: "LVM &amp; Software RAID - Redundant?"
date: 2008-02-02
forum: Desktop Environments
---

### Post by Irrawaddy on 2008-02-02
So I currently have a 200G harddrive that is fast approaching capacity.  I'm planning on adding extra storage and thought to use this as an opportunity to learn about LVM & RAID.  I'm currently planning on adding 3 more drives to my system - another 200G (match the current one) and 2 more 500 or 750G drives.  My /  & /boot will still be located on the existing 74G raptor drive.

At first I thought to use RAID 1 - the data on these drives will not be backed up for a variety of reasons (not critical data), but a RAID 1 would provide a smidge of protection against single HD failure.  I have a P965-DS3 - it has "fake RAID", so I honestly had thought to use mdadm.  Then I started reading about LVM2 - this sounds great, pools of data, managed as one large system rather than independent devices.

In my perusal of the intertubes, I stumbled across many blog posts/how-tos regarding setting up LVM on top of a RAID system.  

Is that really necessary in my case given LVM2 can do mirroring / striping?  Wouldn't LVM on top of mdadm add MORE overhead and not give me any advantages? 

Am I missing something, or is LVM on top of RAID only used with a true hardware controller RAID setup?  Or if I wanted do do RAID 5 or RAID 0+1 (or 1+0).

Given that I'm not interested in anything fancy, will simple LVM2 suffice, or should I look harder at the LVM on top of RAID setups?  Am I missing anything?

Thanks for the help.

-Tony

---

### Post by adeeln on 2008-02-19
LVM & RAID is all about adding maximum flexibility to your RAID array. From my readings, it seems that LVM alone does not provide any of the recovery tools/techniques mdadm provides. LVM's mirroring/striping (to me at least) seems more like a simple RAID1 or RAID0 implementation, while mdadm allows for fancier things, e.g. RAID5/6/etc.

Having LVM & RAID does increase overhead (although all the benchmarks i've seen are fairly dated and may no longer be accurate), but it depends upon what functionality you're looking for. 

In clarification, you mentioned you were thinking of doing RAID1, I believe you mean RAID0 as RAID1 is mirroring, while RAID0 is striping, with no parity, and no redundancy (if one drive goes, the entire array goes). If you're not particularly concerned with disk redundancy, then LVM alone should suffice, imho.

---

### Post by Irrawaddy on 2008-02-19
I ended up going the MDADM + LVM route.  Mostly because based on all of the guides I read, it looked easier to recover from a single disk failure at the MDADM level rather than at the LVM level.  I couldn't find anything conclusive regarding the overhead.  It intuitively makes sense that two software layers would be slower than one software layer.  But I couldn't find any hard data.

I did go for redundancy (this is a data drive), so I have 4 disks in  2 RAID1 mirrors, which are the aggregated into an LVM group.

This is the guide I followed:

[https://help.ubuntu.com/community/Installation/RAID1+LVM](https://help.ubuntu.com/community/Installation/RAID1+LVM)

I had to change a few steps because one of my 4 disks was already in use.  So I built one of the raid1 mirrors with only one disk and then added it later once all of the data was off.  Went very smoothly.

---

### Post by perspectoff on 2008-02-20
The Netgear RAS is a RAID network attached storage device that is expandable from 2 drives (RAID1 generally) to 4 drives (RAID5). It uses Linux as its device internal OS to control RAID.

It is a sweet system and appears to any computer system as an independent drive, with storage up to over a terabyte.

In man-hours, hair pulling, and worry, it is very worthwhile compared to "grow your own" expandable raid systems. 

(No, I don't work for Netgear.)

---

