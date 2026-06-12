---
title: "Freshing install is coming, what to backup? other advice?"
date: 2006-01-12
forum: General Help
---

### Post by naked on 2006-01-12
I've decided it is time for a fresh install.  

I'm definately going to backup my home dir and /etc... but what else?  

As far as new partitioning, I'm going to have maybe 5-10gigs for windows (some programs I RARELY use for work and for 'just in case'), 5g for my home dir, and then rest to ubuntu.  Sound Good?

Anyone else have any advice before I do this this weekend?

L

---

### Post by Sef on 2006-01-13
How big is your hard drive?  

Mine was 20 GB and I did it like this:

Windows 5.0 GB
Ubuntu   5.0 GB
Root        4.5 GB
Home     5,5 GB
Swap       1.0 GB  (512 RAM)

If you want to read up on dual booting, read Herman's write up:

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by naked on 2006-01-13
I have a 40G drive.  

I have 1.25G of ram, so I should do around a 2G swap, but I don't think my swap really is ever used?  I have a swap monitor that I watch and nothing ever seems to change, and it is always DEAD low.  Eh?

L

---

### Post by Sef on 2006-01-13
You don't need that much swap unless u do like heavy duty movie editing.  You can make your swap smaller, and all will be well.

---

### Post by southernman on 2006-01-13
If it were my system, I'd do:

10GB Windows
10GB /
10GB /home
1GB SWAP
9GB (balance of drive formatted during ubuntu install as a VFAT so you can read/write files in windows or ubuntu)

Your mileage may vary...

---

### Post by Aaron Hoy on 2006-01-13
I currently have a small portion of my harddrive for windows, but I am thinking about doing away with it.  wine can run an amazing number of programs if you take the time to get it set up right.  I heard a while ago that Half-Life 2 runs perfectly in wine, and in my experience alot of things have run that I didn't expect to.  If you aren't worried about performance and just want to be able to use windows every once in a while, you also might consider just installing it in vmware.  what way you can bring up windows whenever you want without shutting down linux.  
just a few ideas.

---

### Post by towsonu2003 on 2006-01-13
could as well be

10GB Windows
5GB /
21GB /home
1GB SWAP
3GB FAT32 (in-between partition)

as for the backup, don't know...

---

