---
title: "RAID5 Array Question"
date: 2009-05-15
forum: General Help
---

### Post by Captain Rotundo on 2009-05-15
I am setting up a simple file server that I will start with 3 1TB drives in, with the ability to grow the size later.

I was going to setup a simple raid-5 across the three disks, but have seen in several locations the recommendation to do multiple arrays, so I would for example have 4 raid-5s each made from 3 250GB partitions, one on each disk - them combine the 4 drives back into one logical volume. 

I have seen several explanations that seem to make sense given reasons why this might be good, stuff about adding different sized disks, or bad sectors on part of a disk giving slightly more resiliency until a replacement/rebuild is done. The thing is these all strike me as seeming like false comfort and a single array would be just as 'stable' but I can't quite put my finger on it.

So does anyone have any input on the two methods?

---

### Post by dcstar on 2009-05-15
> **Captain Rotundo said:**
> I am setting up a simple file server that I will start with 3 1TB drives in, with the ability to grow the size later.

I was going to setup a simple raid-5 across the three disks, but have seen in several locations the recommendation to do multiple arrays, so I would for example have 4 raid-5s each made from 3 250GB partitions, one on each disk - them combine the 4 drives back into one logical volume. 

I have seen several explanations that seem to make sense given reasons why this might be good, stuff about adding different sized disks, or bad sectors on part of a disk giving slightly more resiliency until a replacement/rebuild is done. The thing is these all strike me as seeming like false comfort and a single array would be just as 'stable' but I can't quite put my finger on it.

So does anyone have any input on the two methods?

RAID-5 is to protect against data loss when there is a hardware failure in one (only ONE) of the devices in the array - all the data is still available in the remaining RAID devices but you must replace the faulty device to restore any redundancy whatsoever.

Having multiple partitions across the same quantity of physical devices to somehow improve things doesn't make much sense, as you are still at the mercy of the same risk of failure of one of the devices.

Be aware that combining three devices with a MTBF of 10,000 hours each (as an example) gives you a RAID array with a MTBF of 3,333 hours - the more devices you have in any RAID array the more chance that there will be a failure in that array, that is a statistical truth that cannot be avoided.

---

### Post by Captain Rotundo on 2009-05-18
I am completely aware of the mean time to failure problem with RAID, what I am looking to remedy is the "one failure = catastrophic failure" issue!

Are you making a suggestion against RAID-5? or against RAID altogether?

---

### Post by Captain Rotundo on 2009-05-18
Just to be clear, here is the partitioning I was taking about as described on slashdot some time ago - I have seen it elsewhere in slight variations: - The question is, is there  any validity to this setup.

[http://ask.slashdot.org/article.pl?sid=04/10/30/184256](http://ask.slashdot.org/article.pl?sid=04/10/30/184256)

You will get responses from people with good and bad experiences, but they are all jaded by their small particular case. After seeing what can happen with dozens of machines (8 drive and 4 drive) running Linux software RAID5, here is some concrete advice.

First, ensure that all of the drives are IDE masters. Don't double up slaves and masters.

Secondly, DON'T create gigantic partitions on each oft he 250's and then RAID them together, you will get bitten, and bitten hard.

Here's the skinny...

1) Ensure that your motherboard/IDE controllers will return SMART status information. Make sure you install the smartmon tools, configure them to run weekly self tests, and ensure you have smartd running so that you get alerted to potentially failing drives ahead of time.

2) Partition your 250GB drives into 40 GB partitions. Then use RAID5 to pull together the partitions across the drives. If you want a giant volume, create a Linear RAID group of all of the RAID5 groups you created and create the filesystem on top of that.

Here's why, this is the juice.

To keep it simple, let's say there are 20 secotrs per drive. When a drive gets an uncorrectable error on a sector, it will be kicked out of the array. By partitioning the drive into 5 or 6 partitions, let's say hd(a,c,e,g,i,k,l)1 are in one of the RAID5 groups, which contain sectors 1-4 (out of the fake 20 we made up earlier)

If sector 2 goes bad on /dev/hda1, Linux software RAID5 will kick /dev/hda1 out of the array. Now, it's likely that sector 11 might be bad on /dev/hdc. If you hadn't divided up the partitions, you would lose a second disk out of the array during a rebuild.

By partitioning the disks you localize the failures a little, thus creating a more likely recovery scenario.

You wind up with a few RAID5 sets that are more resilient to multiple drive failures.

If you are using a hot spare, your rebuild time will also be less, at least for the RAID5 set that failed.

I hope this makes sense.

My advice to you is to bite the bullet and simply mirror the disks. That way, no matter how badly they fail you'll have some chance of getting some of the data off.

---

### Post by stefangr1 on 2009-05-18
The problem with one filesystem build on a combination of 4x a RAID 5 array is that the entire system still fails when more than 1 disk drops out. Only, with 12 disks the chance that one will fail is much larger!

Some time ago I did quite some research to this subject, and the result was that I didn't take raid 5. It is slow. Reports on the performance of software raid 5 are very mixed and not seldom in the "worst case scenario" range. Also, I noticed too many reports on disks dropping out regularly (sometimes even when rebuilding, in which case all data is gone). Again, failures are overrepresented on the fora, so I'm not sure how I should interpret it. Also, the flexibility of being able to extend the array in a few years (when 2TB isn't that much anymore) is only theoretial, since the risks of resizing the array without being able to backup is very large.

What I would recommend you is to use mirrored raids of just 2 disks, and add new arrays if you want to extend it.

---

### Post by fjgaude on 2009-05-19
Well, folks like, dcstar, point the direction. Many of us have used **mdadm** raid since the beginning in 2002... those that are satisfied with software raid seem to have been those who start with good SATA drives controlled by modern, no older than four years, motherboards.

With raid5 all drives in the array get used identically, so the wear is equal. My feeling is when one drive fails you should replace all! If data is important and drives are so cheap such is the "ticket to ride".

Software raid can be fast, very fast, if CPU and memory are also. I don't use partitions bigger than 320GB because of sync time, **fsck**, etc. I use three levels of backup using **Grsync** and **Unison**, depending if it's a laptop or not. One backup is online, another near-line, and finally, one off-line. Data is that important to me, original graphic designs, notice my signature.

Backup no matter what! If you wish the simple route use raid1, or raid10 for a little more speed. But still have backup storage for those emergencies. Believe me in-time they will happen, no matter what. If you only knew what banks do to protect their data from hardware failure. Just think about it! <smile>

Enough said!

---

