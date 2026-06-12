---
title: "EXT vs. NTFS, space usage (NTFS better?)"
date: 2006-03-20
forum: Desktop Environments
---

### Post by pwrstick on 2006-03-20
This is very interesting to me.  Are these expected results?  I have two identical 200GB SATA drives that I'm in the process of converting to EXT3 (I'm trying to make the switch from XP).  Currently, both drives have the exact same data on them*.  One is still NTFS, and the other is newly EXT3.

But check this out (removed irrelevant drives):

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             184G  169G  5.7G  97% /media/sda1  (EXT3)
/dev/sdb5             187G  169G   18G  91% /media/sdb5  (NTFS)

Why would this be?!  It appear sthat I'm losing a full 12.3 gigs by switching to EXT3, as well as what appears to be another 3 gigz for simply having the EXT3 file system on an empty drive, for a total of 15 gigs.

Is this to be expected, or am I doing something wrong?

Thanks!

*[SIZE="1"]Why?  In preparation of converting my two 200 giggers, I copied all the data from one NTFS HD onto the other NTFS HD, formatted that empty hard drive to ext3, and then copied everything from the NTFS drive to the ext3 drive.  The next step was, of course, to delete the final NTFS partition and convert that to ext3 as well, ending up with two ext3 drives and no data loss.[/SIZE]

---

### Post by cilynx on 2006-03-20
The only thing I can think of is that ext3 keeps a journal of changes.  I don't honestly know how much space that takes up though.

---

### Post by professor_chaos on 2006-03-20
I think that system partitions keep a part reserved for root. For running system tools (fsck, etc) even when the partition is filled to 100%. This is to only thing I can think of.

---

### Post by cilynx on 2006-03-21
That would be it.  I should have thought of that.  ext3 reserves 5% by default for root's exclusive use.  It prevents things like the cycle of doom when the system logs that it's out of disk space.

---

### Post by pwrstick on 2006-03-21
Just for fun:

sda1: ext3
sdb1: reiserFS

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             187G  168G   19G  91% /media/sdb1
/dev/sda1             184G  169G  7.9G  96% /media/sda1


I copied all the files from sda1 directly to sdb1 after turning sdb1 into a reiserfs partition.

---

### Post by robertmcox on 2006-06-22
Both Reiser and NTFS store small files directly in the journal, not wasting whole blocks on files that would fit in less than a block.

I don't believe ext3 has this ability.

---

