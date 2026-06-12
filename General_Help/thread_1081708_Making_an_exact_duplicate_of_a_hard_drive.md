---
title: "Making an exact duplicate of a hard drive?"
date: 2009-02-26
forum: General Help
---

### Post by gtg947h on 2009-02-26
I just set up a home server whose hard drive is completely encrypted (except for /boot).  I'd like to make a weekly backup of *everything* on that drive, and keep it encrypted.  In essence, I want a byte-for-byte duplicate of the primary drive, so that if said primary drive fails, I can just replace it and restore it from the backup.  The backup drive is an external USB drive with the same capacity of the internal drive.

Any suggestions?

Thanks!

---

### Post by taurus on 2009-02-26
Not sure if Clonezilla and/or PartImage can handle an encrypted harddrive.

[http://www.clonezilla.org/](http://www.clonezilla.org/)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Slim Odds on 2009-02-26
> **taurus said:**
> Not sure if Clonezilla and/or PartImage can handle an encrypted harddrive.

I don't see why not. As far as they are concerned it's just data.

Once it's on the new drive, then he'll need the proper drivers and key.

---

### Post by dcstar on 2009-02-27
> **gtg947h said:**
> I just set up a home server whose hard drive is completely encrypted (except for /boot).  I'd like to make a weekly backup of *everything* on that drive, and keep it encrypted.  In essence, I want a byte-for-byte duplicate of the primary drive, so that if said primary drive fails, I can just replace it and restore it from the backup.  The backup drive is an external USB drive with the same capacity of the internal drive.


The dd command/pcopy package can do this for individual partitions or the whole disk, the Partition Manager can copy individual partitions.

---

