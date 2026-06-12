---
title: "RAIDing only the Home directory"
date: 2010-01-14
forum: Desktop Environments
---

### Post by fester225 on 2010-01-14
I'm installing a second hard drive for use as a RAID1 drive. Is it possible to configure my RAID1 drive to only backup my Home directory?

---

### Post by falconindy on 2010-01-14
I think you're misunderstanding how RAID1 works. It's not a backup. Again, RAID is not a backup.

A level 1 array takes two drives (or more) and combines them into what appears to be a single drive, with the resultant size being equal to the size of the smallest drive. Data is mirrored across all drives in the array. In case one of these drives fail, the throws an error up, but remains accessible as long as it still has at least 1 healthy drive.

If you wanted to create a RAID 1 array for only /home, you could do this:

1) Carve out 10gb (or however much you want) partitions on each of 2 physically separate drives. 
2) Create a RAID1 array device using these partitions.
3) Format it with your filesystem of choice
4) Mount it as /home

---

### Post by wlraider70 on 2010-01-14
Are you saying that i could set a raid to 2 partitions on the same drive?

---

### Post by pirateghost on 2010-01-15
> **wlraider70 said:**
> Are you saying that i could set a raid to 2 partitions on the same drive?
its possible but WHY?

the reason for RAID is in case of HARDWARE failure, if your SINGLE drive failed what good did the raid do?  all you are doing is taxing the drive more by forcing the different partitions to do more than they are intended and you shorten the lifespan

i will reiterate what was already said:

RAID IS NOT A BACKUP SOLUTION

---

### Post by fester225 on 2010-01-15
So.....you have multiple copies of the files in your system on separate drives, the idea being to avoid permanent data loss, and this isn't a backup solution?

Perhaps I would be better off asking: How do I get my system to automatically make a second copy of the files I have in my Home directory on a second drive?

---

### Post by falconindy on 2010-01-15
> **wlraider70 said:**
> Are you saying that i could set a raid to 2 partitions on the same drive?
You could, but a high access drive will hate you for the remainder of its short life. You skipped over the words "physically separate drives" in my description above.

> **fester225 said:**
> So.....you have multiple copies of the files in your system on separate drives, the idea being to avoid permanent data loss, and this isn't a backup solution?
If you consider that to be a backup, then so be it. Personally, I don't. It won't save you in the event of:
1) Multi device failure (e.g. a PSU shorting out)
2) Natural disasters
3) Theft

This is why offsite backup companies are in business.

---

### Post by pirateghost on 2010-01-15
> **fester225 said:**
> So.....you have multiple copies of the files in your system on separate drives, the idea being to avoid permanent data loss, and this isn't a backup solution?

Perhaps I would be better off asking: How do I get my system to automatically make a second copy of the files I have in my Home directory on a second drive?


if you want to have multiple copies of / why use partitions?  just set the system up on one big RAID1 configuration...

by partitioning and raiding, you are essentially taxing your harddrives beyond what they are designed for....its just not a good practice
if you want to RAID, then make the whole thing a raid setup and forget about it, however, this does NOT prevent human errors, like uninstalling packages that were not supposed to be uninstalled, dickin with your grub+kernel ....  RAID is designed more for less downtime/loss of data in case of physical problems (failures, bad sectors, etc)

if you want a backup, set up some syncing software to sync the contents of your important data to another drive, but just dont think that RAID is a backup...its the wrong way to think

---

### Post by JackRock on 2010-01-16
The reason RAID is not a backup solution is because the data is written *simultaneously* across all the configured drives, partitions or separate. The purpose of backing up data is to save the data itself.  So, with RAID, the moment you cause something to be irretrievably lost, it is lost EVEN ON THE RAID.  So, it's not a backup, because a backup is meant to be restored to the last backup, whenever that was.

So since RAID writes simultaneously, any errors in coding/writing also fail simultaneously on the "backup".  So your "backup" would have all the same problems that your "main" had....down to the last detail.

RAID protects ACCESS to that data in the case of hard disk failure only (it doesn't necessarily protect against other hardware defects, unless they, too, have redundancy measures implemented).  It allows you to get to the most recent saved data if one of the hard drives fails.

So I must agree with pirateghost.  A 3rd-party backup solution for your /home/ folder is the best option, since I do not believe Ubuntu includes one in the distro.  If there is, I haven't found it, yet.

The ONLY circumstance your RAID1 would function as an effective backup is if ALL of the situations occur:
1.  The RAID is configured across at least two PHYSICALLY SEPARATE drives
2.  One of those physical hard drives fail and is no longer operable.
3.  You obtain a THIRD physical hard drive, install Ubuntu on that drive, and mount BOTH drives so they are accessible to the computer.
4.  You peruse and copy the /home/ directory files as you see fit.

So, you see, that the RAID situation functions as a "backup" only if a VERY specific set of circumstances occur.  BUT, that's redundant to the point of being ludicrous, because if Hard Drive #2 hasn't physically failed, it should still accessible as a wholly separate installation of Ubuntu and all saved files.  You would need then to make it your primary drive, and then RAID it to another (that third) physical hard drive.

---

