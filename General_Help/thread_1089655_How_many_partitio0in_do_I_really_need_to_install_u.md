---
title: "How many partitio0in do I really need to install ubuntu?"
date: 2009-03-07
forum: General Help
---

### Post by mcnr on 2009-03-07
I have a 20gig partition set up and another 6gig on first partition on another drive for the swap will Ubuntu live with this?  I can make a third but it's a hassle.  To dual boot do I need to have XP and Ubuntu on master drive or can it be master/slave?  What order should the drives be in?  Should Ubuntu be before XP as far as boot sequence? They are all SATA.

Marc

---

### Post by hexanol on 2009-03-07
In the SATA world, there's is no master/slave relationship between drives.

XP has to be installed in a primary partition. I think it can be installed on any drive, but i'm not 100% sure. For Ubuntu, you'll be fine with 2 partition (you could even make it with only 1 even if it's not recommended that much). Personnaly I would install XP on your first drive (i.e. the boot drive). Install Ubuntu wherever you want. Same thing for the swap, can be on any drive in any kind of partition.

---

### Post by mcnr on 2009-03-07
I have XP on the first partiton on the primary boot drive.  I have another partition marked as active first partition on another drive for Ubuntu and swap files for both XP and Ubuntu on the first partitions of a third and fourth drive.  Does the XP and Ubuntu drive need to be in a certain order?  Do I need a third partition for Ubuntu for programs and data?

Marc

---

### Post by HermanAB on 2009-03-07
Howdy,

Multiple partitions are only essential on a server.  A home machine can do with a single partition and a swap file.  However, I always create a /home partition.  The reason being that if all your data is always in /home, then you can upgrade and re-install Linux without wiping out your data - just don't format /home and you are good to go.  It also makes it easy to do backups - simply backup all of /home and you are done.

On a server, multiple partitions guard against runaway problems that can fill up a whole partition with crud in the blink of an eye. If / would become full, the server will be unbootable, so it is wise to break things up and limit the potential damage.

Cheers,

Herman

---

### Post by hexanol on 2009-03-07
Ubuntu is fine with 2 partitions. You can create more, but that's not necessary in a normal use. If you want to create a data-only partition, than that's your call. But with 4 drives, I guess you already have data-only partitions, no ?

Just be sure that the drive where XP is installed is the first drive and there's should be no problem. Ubuntu can be installed in any way (on any drive, in any kind of partition (primary, logical).

---

### Post by jwbrase on 2009-03-07
> **hexanol said:**
> 
Just be sure that the drive where XP is installed is the first drive and there's should be no problem. Ubuntu can be installed in any way (on any drive, in any kind of partition (primary, logical).

Windows needs to be on the first drive, but which drive is first can be reassigned by Grub when Windows is selected with 
```
map (hd0) (hdx)
map (hdx) (hd0)
```

With hdx being the drive Windows is on (hd1, hd2, or whatever).

---

