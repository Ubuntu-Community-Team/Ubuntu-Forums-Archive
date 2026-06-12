---
title: "Partitioning help needed"
date: 2009-05-19
forum: General Help
---

### Post by pete_mcal on 2009-05-19
Hey I have an external hard drive which my friend tried to install ubuntu to boot from a partition so I could have ubuntu on my eee pc and have the internal hd for storage only and keep a storage section on my external. In the process he also created a separate secondary storage partition for what reason i do not know. 

Anyways the whole thing was an epic fail and now I want to return my external HD to one big partition without losing the data on main partition. 

the hard drive looks as follows [IMG]http://i685.photobucket.com/albums/vv214/petemcal/Screenshot2.jpg[/IMG]

I tried installing a nfts config tool that someone suggested on the forums but i dont know if it was the right version for my os as when i click it nothing happens here is my system if it helps any [IMG]http://i685.photobucket.com/albums/vv214/petemcal/system.jpg[/IMG]

So i want to join the other sections onto the 385gb but not lose my data

thanks in advance ;)

---

### Post by dstempfley on 2009-05-19
Just in case... Boot windows and run a disk scan and shutdown cleanly.  This will take a couple of boots.  one to mark for check, then one to do the scan on reboot.

or run fast and loose and skip the disk check.  Your choice.

use gparted and delete all the partitions you don't want.
The resize the primary partition to fill the entire disk.

That's it

/Dion

---

### Post by blacksm1th on 2009-05-19
> **pete_mcal said:**
> ...
The safest way to do that - copy this ~160GB to internal HDD and then delete all partitions on external. Then create one new big partition on external. Any other method hide risks for data. 
But if you like risk - install "ntfsprogs" from Synaptic and then resize the big ntfs partition with gparted (delete other partitions first).

---

