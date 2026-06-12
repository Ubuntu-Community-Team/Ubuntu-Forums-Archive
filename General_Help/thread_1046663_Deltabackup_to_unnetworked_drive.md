---
title: "Deltabackup to unnetworked drive"
date: 2009-01-21
forum: General Help
---

### Post by Breepee on 2009-01-21
I'm in the following situation:

I have a dataset on a local drive, which is about 1.25TB at this moment. It's a collection of files I want to have backed up offsite. Normally you'd think rsync or rdiff(-backup), but the caveat is that the drive to back up to isnt connected to a network. I'll need to take the changes with me through sneakernet, typically every two to three weeks.

So, what I'm looking for is this: a system that allows me to take only the changes to the dataset (which typically will be in the order of a few GB's) with me on an USB drive. The system will apply them on the backup dataset to bring it in complete sync with the originals on the local master drive.

Because I don't need it, and because it would take up too much space, I don't need the system to keep a record of changes made, through hidden directories with deltafiles of something like that. Just make the stream of bits on the backup drive match the stream of bits on the master drive.

I imagine this works as follows: initially, I sync the drives manually by moving the physical backup drive to my local system and simply copy the master to the backup.

At this point I let the system make somekind of snapshot, based on (rolling) checksums of the data. At the time I decide to create sync up the backup, the system can generate a deltafile which I can transport on and usbdrive. Then, on the backup drive, I can apply it so that the backup matches the master. At this point, I create a new snapshot from the master (decard the old one) and the cycle starts anew.

Any ideas if this is possible and how I could achieve this?

---

