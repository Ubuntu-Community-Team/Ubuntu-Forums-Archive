---
title: "EXT3 external hard drive keeps going read-only with Deluge"
date: 2009-04-07
forum: General Help
---

### Post by mtopro on 2009-04-07
I have Ubuntu 8.10 with several 1 TB external hard drives (all ext3) for extra storage.  Recently one of the drives that I use for downloads will suddenly turn read-only after a few minutes of Deluge running.  Not sure what is the root of the issue but the only way I can fix it is by rebooting the system.  Unmounting and remounting the drive does not seem to fix the read-only issue.  Tried chmod and chown but these run through all the files and error with read-only.

I can't think of any settings that were changed recently, and I keep a log of changes that I make.  The only thing I can think of is maybe an update created the issue but I can't find a bug in Launchpad that matches my problem.

Any ideas?

---

### Post by mtopro on 2009-04-07
seems it may have something to do with the number of simultaneous downloads?

---

### Post by mtopro on 2009-04-11
maybe something to do with the MP3s that I'm trying to download..

---

### Post by mtopro on 2009-05-17
I thought the hard drive was EXT3 since that is what all my other drives are..  But recently I discovered it was actually FAT32.  After reformatting the drive to EXT3 the problem no longer exists.

---

