---
title: "Hard Drive Recoverty"
date: 2008-12-24
forum: General Help
---

### Post by kooseefoo on 2008-12-24
So, I was reformatting an ext3 partition on my hard drive to NTFS.

I reformatted the wrong one.

I haven't done any writing to the disk since. So, the table of contents should be the only thing modified.

Ideas?


Chris

---

### Post by oilchangeguy on 2008-12-24
> **kooseefoo said:**
> So, I was reformatting an ext3 partition on my hard drive to NTFS.

I reformatted the wrong one.

I haven't done any writing to the disk since. So, the table of contents should be the only thing modified.

Ideas?


Chris

you can try this:
[http://blogs.sun.com/superpat/entry/hard_drive_recovery_ubuntu_style](http://blogs.sun.com/superpat/entry/hard_drive_recovery_ubuntu_style)

---

### Post by kooseefoo on 2008-12-24
Thanks. This is going to be a long night before Christmas...

Speaking of which, MERRY CHRISTMAS!

---

### Post by kooseefoo on 2008-12-25
I tried ddrescue.

First, I created a new partition on another drive that was larger than the partition I'm recovering. Then, I just ran:

ddrescue /dev/screwedup /dev/newpartition

It ran through pretty quickly. Got nothing so far though. Will ddrescue actually try to recreate a table of contents?

---

### Post by kooseefoo on 2008-12-25
Ok, now that I've calmed down a bit, I think I know what I'm doing. ddrescue is meant for hardware failures, and just copies everything it can find on the disk. So, I created a clone of my messed up data (not a bad thing. Just gives me a worry-free playground for fixing this).

So, now I need a file recovery/undelete utility. Unfortunately, I'm not sure how my reformatting of the drive will affect this. Since the drive was ext3 and now ntfs... yeah. I have no clue. Should I take my cloned drive and reformat it back? Seems like that can't do any harm...

---

### Post by kooseefoo on 2008-12-25
All the utilities I've looked at so far (foremost, scalpel, etc...) don't seem to recover filenames and locations.

Is there anything that can do that, or does the nature of my mistake inherently stop that from being possible?

---

### Post by Endolith on 2009-01-23
You saw [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), right?

---

### Post by kooseefoo on 2009-02-01
I read through that. I'm still unsure about whether or not I can actually get everything back though. Most of that is about lost partition tables or a crashed drive. I reformatted (quick format) the whole partition.

---

### Post by Endolith on 2009-02-01
I'm not an expert, but 

quick format = optimistic about recovering the data
changing filesystem = pessimistic about recovering filenames and folders

---

### Post by kooseefoo on 2009-02-01
Yeah. I don't want to have to use a tool that searches for things - .jpg files - for instance, and take each one and give it a name. Since I changed the filesystem from ext3 to ntfs, I'm kind of stuck, unless a recovery ninja shows up on this forum.

---

