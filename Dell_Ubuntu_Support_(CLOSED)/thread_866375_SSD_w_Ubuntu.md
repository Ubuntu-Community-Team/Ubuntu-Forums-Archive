---
title: "SSD w/ Ubuntu"
date: 2008-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lee_connell on 2008-07-21
Dell doesn't offer ubuntu based notebooks with the 64gb SSD.  Is there a problem with ubuntu and SSD on DELL?  Would it be ok to purchase a non Ubuntu based DELL notebook with SSD and put Ubuntu on it?

---

### Post by akniss on 2008-07-21
There is no problem.  I have the m1330 with a 32 GB SSD and have had no issues at all with either Gutsy or Hardy.  I ordered mine before they offered Ubuntu on the m1330 (and before they had the 64GB SSD), so I purchased it with Vista, I installed Ubuntu shortly after receiving it.

---

### Post by lee_connell on 2008-07-21
thanks akniss,

how is the performance difference, battery, and quietness on it?

---

### Post by sdennie on 2008-07-21
Though I don't have an SSD, it might be advisable to not use ext3 as the filesystem on it because it will cause excessive writes by default (on the order of every 5 seconds).  Alternatively, you can use ext3 but tweak the system a bit to be less write intensive on the SSD.  You could do that with one of these two guides: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773) or [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).

---

### Post by falcon61102 on 2008-07-21
Vor, 
I'm not the most knowledgeable about SSD but wouldn't it be more beneficial to use SSD instead of a normal HD because with an SSD you won't run into the problems of excessive disk activity eventually ruining the drive?

Also, I know ASUS has been making the EEEPC for a while with SSD drives and Linux on them.  From the research I've done on them, they don't seem to have any problems handling it.

lee_connell,
Due to the nature of an SSD, battery life is normally increased because it takes less power to run an SSD than a HD.  It is definitely more quiet because you won't have physical parts moving around, which also makes it more durable against shock.  And performance is normally slightly greater because again, there are no moving parts that have to get into place before a read/write can be accomplished.  While this boils down to milliseconds, it's something... :).

From what I've seen with SSD's right now, the biggest downside to them is their size and cost.  But as with all hardware, that's temporary as they become more common.

Just my two cents. :)

---

### Post by sdennie on 2008-07-21
> **falcon61102 said:**
> Vor, 
I'm not the most knowledgeable about SSD but wouldn't it be more beneficial to use SSD instead of a normal HD because with an SSD you won't run into the problems of excessive disk activity eventually ruining the drive?


Well, excessive disk writes can shorten the life of an SSD as well.  They don't have problems with the infamous Load_Cycle_Count issue but, as I understand it, each "cell" in an SSD is only rated for a certain number of writes.  The disk itself will do wear leveling to help increase the lifetime of the drive but, the constant writing of ext3 journal commits every 5 seconds or so certainly isn't beneficial to disk life.  Now, whether or not it will shorten the life to something less than it's effective usefulness, I don't know.

---

### Post by falcon61102 on 2008-07-21
Yeah, I agree with you.  Either way the 5 second commits are going produce wear on whatever drive they are going to whether SSD or normal.  I like the speed and shock factor.  

I've had too many drives go out on me due to my traveling so it's nice to see something a little more durable.  And I'll take more speed anyday when it comes to moving data.

---

### Post by sdennie on 2008-07-22
> **falcon61102 said:**
> Yeah, I agree with you.  Either way the 5 second commits are going produce wear on whatever drive they are going to whether SSD or normal.  I like the speed and shock factor.  

I've had too many drives go out on me due to my traveling so it's nice to see something a little more durable.  And I'll take more speed anyday when it comes to moving data.

I certainly agree with the speed/durability aspect.  Though, I must say that with people buying machines (even laptops) with 2GB or 4GB of RAM, after a day of normal usage, disk speed isn't much of an issue for most people because almost everything you need is cached in memory anyway.

Having said that, I still plan to upgrade to an SSD in the near future.  :)

---

### Post by falcon61102 on 2008-07-22
Yeah, good point.  I'm planning to get one for an external so I don't have to worry about being as gentle with it as I do a regular drive.

---

### Post by dicecca112 on 2008-07-22
> **vor said:**
> I certainly agree with the speed/durability aspect.  Though, I must say that with people buying machines (even laptops) with 2GB or 4GB of RAM, after a day of normal usage, disk speed isn't much of an issue for most people because almost everything you need is cached in memory anyway.

Having said that, I still plan to upgrade to an SSD in the near future.  :)

In theory your right, but not in practicality.  Unless your righting in excess of 5GB of data a day, your not going to harm your SSD.  You should be more concerned about heat. I had a Supertalent MasterDrive MX in my Dell, and it was fried due to heat.  To the OP I've used a 60GB Supertalent and am now using a 64GB OCZ Core 2 SSD.  Both work fine.  But a word of warning, shut off ACHI, only then will you get the correct read and write speeds.

---

### Post by sdennie on 2008-07-22
> **dicecca112 said:**
> In theory your right, but not in practicality.  Unless your righting in excess of 5GB of data a day, your not going to harm your SSD.  You should be more concerned about heat. I had a Supertalent MasterDrive MX in my Dell, and it was fried due to heat.  To the OP I've used a 60GB Supertalent and am now using a 64GB OCZ Core 2 SSD.  Both work fine.  But a word of warning, shut off ACHI, only then will you get the correct read and write speeds.

For an SSD, I don't think it's the size of writes that matters but the frequency.  If you write a 10GB chunk to an SSD in one shot, it's not a problem.  If you write 1k every 5 seconds all day, every day, it's dangerous.

---

### Post by dicecca112 on 2008-07-22
Not according to OCZ and SuperTalent.  If you go to SuperTalents website, there is a whitepaper on the subject.  Same with OCZ

---

### Post by sdennie on 2008-07-22
I'll be happy to look at the links if you provide them.

From what I've read from independent sources (i.e. not disk vendors), when you write to an SSD, it doesn't write to the same spot the data was previously stored but to the least worn out part of the SSD (this is called wear leveling).  Each "spot"/"cell"/"block" in an SSD can take a limited number of writes before it degrades (though, that number can be very high these days).

Keeping that in mind, writing a 10GB file to the SSD once per day causes almost no degradation.  Writing a single byte to the SSD once per second is much, much harsher on the SSD even though it only amounts to 3.6k worth of data.  (That's a contrived example.  The disks might having something in place to prevent that worse case scenario).

---

### Post by dicecca112 on 2008-07-22
> **vor said:**
> I'll be happy to look at the links if you provide them.

From what I've read from independent sources (i.e. not disk vendors), when you write to an SSD, it doesn't write to the same spot the data was previously stored but to the least worn out part of the SSD (this is called wear leveling).  Each "spot"/"cell"/"block" in an SSD can take a limited number of writes before it degrades (though, that number can be very high these days).

Keeping that in mind, writing a 10GB file to the SSD once per day causes almost no degradation.  Writing a single byte to the SSD once per second is much, much harsher on the SSD even though it only amounts to 3.6k worth of data.  (That's a contrived example.  The disks might having something in place to prevent that worse case scenario).


There are algorithms in place that write to the disk to prevent this.  I'm just echoing what OCZ and SuperTalent told me, as far as I know, it could be BS.

[http://www.supertalent.com/datasheets/SSD_WHITEPAPER.pdf](http://www.supertalent.com/datasheets/SSD_WHITEPAPER.pdf)
[http://www.supertalent.com/products/ssd_detail.php?type=MasterDrive%20MX#](http://www.supertalent.com/products/ssd_detail.php?type=MasterDrive%20MX#)

---

### Post by sdennie on 2008-07-22
> **dicecca112 said:**
> There are algorithms in place that write to the disk to prevent this.  I'm just echoing what OCZ and SuperTalent told me, as far as I know, it could be BS.

[http://www.supertalent.com/datasheets/SSD_WHITEPAPER.pdf](http://www.supertalent.com/datasheets/SSD_WHITEPAPER.pdf)
[http://www.supertalent.com/products/ssd_detail.php?type=MasterDrive%20MX#](http://www.supertalent.com/products/ssd_detail.php?type=MasterDrive%20MX#)

I'm too tired to wade through them at the moment but I'll certainly look at them tomorrow.  ;)

My guess (without having looked at them at all) is that they consider the default behavior of ext3 to be a fringe case whereas, on Ubuntu (and every other linux distro I've looked at), it's the common case.

---

### Post by dicecca112 on 2008-07-22
You definitely have me worried, and I wonder if that contributed to the death of the drive.  I'll probably reinstall ubuntu with ext2 this weekend.  

And trust me, I'm only 1 cup of tea in this morning, I'm not awake yet either

---

### Post by sdennie on 2008-07-22
> **dicecca112 said:**
> You definitely have me worried, and I wonder if that contributed to the death of the drive.  I'll probably reinstall ubuntu with ext2 this weekend.  

And trust me, I'm only 1 cup of tea in this morning, I'm not awake yet either

Well, I'm not trying to be an alarmist but, the default ext3 settings are very well suited for servers but, unless tweaked, very poorly suited for any type of laptop.  Rather than foregoing any type of journaling at all, I would instead recommend just throttling it back a bit with something like this: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998) (or the XPS m1330 link my signature).  

Pushing all your disk writes from a 5 second interval to a 60 second interval gives an acceptable amount of potential data loss for a laptop (the battery is like an UPS so, if your system is stable, you almost have to try to lose data) but decreases the frequency which the disk is written by a factor of 12.

---

### Post by digicidal on 2009-12-30
Sorry to resurrect this thread, but as SSD adoption becomes more prevalent there will be more users (like myself) getting hits on this thread if they're googling 'ubuntu SSD'.

Although there was initially an issue with shortened life of SSD drives based on flash cell 'death' - that is really not an issue at all with any current drives.  The problem existed (for the most part) on very early drives which were very small (2-5GB) and didn't have any of the comprehensive wear-leveling algo's of todays hardware.

The math is fairly simple here - if the cell life is 100K (which is actually on the low end of current drives... some are 2-5M writes) and the drive is 32GB (also on the low end of current drives) - then the total minimum amount of data required for failures is somewhere around 3.2PB - so at 200MB/sec (very high end for writes) it would take you:

100,000 * 32,000 / 200 seconds to cause failure from sequential writes.... naturally we're assuming no reads are occurring ever because reads don't affect lifespan at all, but do affect interface bandwidth available for writing - thus slowing everything down.  16M seconds = 185 days - not very long perhaps (but remember that this is using the very best drive's transfer speeds, and the very worst drives durability and capacity).

Now you are correct that random writes *might* present more of a problem - however, they actually present less of one as I understand the technologies currently present.  Since even on the fastest and most expensive drives - random writes occur far more slowly than sequential ones.  Usually by a factor of at least 2.5 - since the controllers on SSD's track the number of times each cell get's written to, and perform writes on what amounts to a 'usage stack' (least written cells are used first on any given operation) - it really doesn't matter whether they are random or sequential - it will still use the entire surface for the data.

Now when you consider that the most common PC usage is about 3:1 ratio of reads/writes - even if we believe that the entire transfer bandwidth is being used all of the time - that would still put us out more than a year and a half before we really even need to consider cell death a potential problem.

If you add in that modern manufacturing has extended NAND lifespans to well over 2M write cycles, and the wear-leveling actually marks 'at death' cells as unwriteable - what you get is about 5-6 year lifespans under this fictitious 'worst case' - and then your drive would just start shrinking... i.e it would go from a 32GB drive to a 31.999999GB drive (it would still appear to be a 32GB drive, but the freespace would start shrinking very slowly as cells got marked as unuseable).

In normal real-world conditions - you should be able to run an SSD just like a regular hard drive with no consideration at all - and get about 50 years of life out of it.

However, even in the worst case "realistic" scenario of 4-5years - are you confident that your netbook will still even run then?  I certainly am not - but I would bet that your SSD will still hold data then... and probably for a decade after that as well.

PS - what I had hoped to find in this thread and several others - were ways to tune Ubuntu to be able to best capitalize on the increased speed and decreased seek times of SSD's.  It seems that the SSD Cell Death scare is the primary concern for most people - because that's all I can ever find in my searches.  If you look around now, you can find more information as more and more engineers and OEM's are beginning to understand the stigma that SSD's still have for being "short life dirves" - even though this stopped being the case back in the late 90's actually.

---

### Post by propan0 on 2010-08-02
Thanks for the update on this issue digicidal, very much appreciated.

---

### Post by medeiom on 2011-01-11
I know Windows 7 has the TRIM feature for SSD performance. But how does Ubuntu handle the so called "garbage collection" from Solid State Drives?

---

### Post by gibbylinks on 2011-01-12
Ubuntu supports trim, 10.10 certainly does. There are plenty of threads out there on this if you do a search. :D

---

