---
title: "[SOLVED] XFS not working, or is it mdadm?"
date: 2008-12-23
forum: General Help
---

### Post by Kissell on 2008-12-23
I typically have always use ext3 for linux boxes...  

But, I'm creating a new software raid file server (using mdadm to save cost) to serve up only very large files, and thought I'd give XFS a try...  I ran into two problems.

1) if I create a partition at /dev/md0/p1 the command > mkfs.xfs -d agcount=8 -l size=128m /dev/md0p1 won't work for some reason...  have no idea why, shouldn't it?  So anyway, I just partition the whole md0 disk with > mkfs.xfs -d agcount=8 -l size=128m /dev/md0 and that seems to be okay.

2) after creating the file system i can mount it and start copying files...  works great...  except, if I try to do a large file copy, like if I try to copy more than a few gigabytes then it ALWAYS hangs exactly 10 seconds after initiating the transfer to write this data to the XFS volume.  

Doesn't matter where I transfer the files from or what protocol or program I use, I can transfer files to other devices like /dev/sda, i just can't copy them to /dev/md0 so I want to blame XFS because I have no experience with it...

Although, there is one other thing I did new...  I normally use default 64k block sizes when creating an array with mdadm...  this time I used 1024k block sizes (because there will only be very large files of 1GB or more on this server)...  is that the problem and not XFS?

----------
EDIT:
I meant 1024k chunk size, on the mdadm array creation, not block size :p  Also, the reason I tried to go so big, is this is an 8TB raid volume with only large files...  but I haven't see any posts of anyone else ever going above 256k... or anyone else complaining about XFS locking up...  hmmm....

---

### Post by albinootje on 2008-12-23
> **Kissell said:**
> 
1) if I create a partition at /dev/md0/p1 the command  won't work for some reason...  have no idea why, shouldn't it?  So anyway, I just partition the whole md0 disk with  and that seems to be okay.


With software-RAID in Linux the partitions would be :
```

/dev/md0
/dev/md1
/dev/md2

```
etc.
I've read that it is recommended to let RAID have the whole disk, but perhaps that's for hardware RAID.
I've run a few boxes for more than a year with software RAID on several partitions without problems.

---

### Post by Kissell on 2008-12-23
yeah, i've always done the entire disk, like /dev/md0, but i see in examples online other people are doing /dev/md0p1, and when I do it with the whole disk and I do a fdisk -l /dev/md0 it says 'no partition found on device' yeah, i can format the /dev/md0 and use it with no problems, but i was preferring to use /dev/md0/p1 because i wanted fdisk to not appear so scary with i list the drives.

Anyway, that was just something minor...  my real "problem" is that I can't copy files to the drive...  any sustained transfer hangs up the transfer process.  sucks...

i've seen plenty of posts now with other people using 1024k chunk sizes in mdadm, and i've seen plenty of posts with other people using XFS with my parameters, but i've been unable to find anyone else who's ever had this problem or knows how to fix it.  :(

---

### Post by fjgaude on 2008-12-24
From the man pages:

>  The standard names for partitionable arrays (as
       available from 2.6 onwards) are either of

              /dev/md/dNN
              /dev/md_dNN

       Partition numbers should be indicated by added  "pMM"  to  these,  thus
       "/dev/md/d1p2".

Everytime I've tried to use this feature I've failed.

As to the large file copy issue, it could be a bug. I recall that some of the Linux programs haven't been updated to handle media files in the gigabyte range yet. You might file a bug report. Best of luck to you.

---

### Post by Kissell on 2008-12-24
Well, I couldn't wait any longer, so I kept experimenting...  experimenting was not a happy process, because building the 8TB array takes 30 hours for each try..

Anyway, I got it working with XFS by doing two things simultaneously.

My original try I had 1024k chunk size on the array and had changed the agcount with XFS to 8.  That never worked when trying to sustain large file copy to the array.

The way it's set now, I have 128k chunk size on the array, and have formatted the array with XFS, but not specifying the agcount (left it at default of 32).  With these two modifications it does work

Good enough, it works, don't know why it didn't on the other settings, but it doesn't, and it does on these.  I believe it is a bug, it consistently doesn't work on those other settings and I think it should.

---

### Post by fjgaude on 2008-12-25
Glad the defaults essentially work, but as you know, these other settings have had little use likely, and the developers have little motivation to test all possible settings... simply not enough people in the development pool to correctly test all possibilities.

I know when I was programming nothing worked that I didn't test first and fix. <smile>

File a bug report and see what response you get.

---

