---
title: "Jaunty ext4"
date: 2009-06-21
forum: General Help
---

### Post by measekite on 2009-06-21
Installing Jaunty on an ext3 partition.



How wise and safe is it to use ext4 for your data partition and backup drive?  I hear there has been issues of losing data after a crash with ext4 failing to write.

Is it better to wait for Koala when ext4 will be the default.

Many fedora users are not using the ext4 default even though fedora has done something to rememdy the problem.

---

### Post by DeMus on 2009-06-21
> **measekite said:**
> Installing Jaunty on an ext3 partition.



How wise and safe is it to use ext4 for your data partition and backup drive?  I hear there has been issues of losing data after a crash with ext4 failing to write.

Is it better to wait for Koala when ext4 will be the default.

Many fedora users are not using the ext4 default even though fedora has done something to rememdy the problem.

I use Ext4 and find no problems at all. I use it for all partitions. Works great and seems to be faster than Ext3. Go for it, make make back-ups to be absolutely sure.

---

### Post by Legace on 2009-06-21
> **DeMus said:**
> I use Ext4 and find no problems at all. I use it for all partitions. Works great and seems to be faster than Ext3. Go for it, make make back-ups to be absolutely sure.

+1

I've used Ext4 on Jaunty full-time and no problems at all :)

---

### Post by KeyserSoze93 on 2009-06-21
On the other hand though, what will you get out of using ext4; are the improvements over ext3 really worth losing compatibility?

When I upgraded my laptop to Jaunty - and foolishly went the whole hog by converting my /home to ext4 too - I found the performance was abysmal (maybe it's absolutely fine for some people, but as I found from the thread I started, I wasn't the only one having problems)

When I wanted to switch back to Hardy, which should have been no problem, I had the tedious process of having to format my /home back to ext3, which kind of defeated the point of having a separate /home partition: the fact that your data and personal files are not tied to the operating system install.

If you have any problems with Jaunty, or if you have to us a recovery disk to get data off your hdd, it's probably best to have a filesystem that pretty much every Linux in circulation can deal with.

If you want to try ext4, maybe you should use it for / (root) instead?

---

### Post by wpshooter on 2009-06-21
I am using Ext4 on Jaunty, no problems here.

---

### Post by ad_267 on 2009-06-21
I don't think you'd gain much using ext4 on your backup drive, you might as well use ext3 on that as you probably want to minimize the risk of anything going wrong there. I'm using ext4 on my root partition and ext3 for my /home here and haven't had any problems so far.

---

### Post by Arup on 2009-06-21
ext4 here from day one of Jaunty release, no issues at all whatsoever.

---

### Post by pmbuc on 2009-06-21
Yesterday, I had to reinstall Hardy after a couple of days of some helacious performance and stability issues with Jaunty on a Dell Inspiron 6000. (I always do clean installs, by the way.) I was using ext4 for root and home partitions, so I had to back up my configs and personal data due to the reformatting of home. Was ext4 the cause of my instability and persistent lockups? Maybe. Maybe not. All I know is that Jaunty has failed to perform well on two Inspiron laptops of different age groups. Hardy runs very well on both, so release changes are obviously the culprit. I would second the recommendation to keep home as an ext3 partition, if your data is that important to you.

---

### Post by theozzlives on 2009-06-21
I have 2 computers with ext4 (one with a ext3 /home). I swear by the performance increase, if you have doubts, just format the root (/) with ext4.

---

### Post by lovinglinux on 2009-06-21
Don't get me wrong, but do we really need another thread about this?

[Ext3 and Ext4: Which file system to install?](http://ubuntuforums.org/showthread.php?t=1133719)
[have you had any problems with ext4?](http://ubuntuforums.org/showthread.php?t=1170802)
[Should I switch to ext4?](http://wwww.ubuntuforums.org/showthread.php?t=1157658)
[Choosing ext4 over ext3](http://ubuntuforums.org/showthread.php?p=7209536)
[Jaunty and EXT4](http://ubuntuforums.org/showthread.php?t=1180097)

**Quick links to similar threads:** [Google Site Search](http://www.google.com/search?q=ext4+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0) | [Forum Search](http://ubuntuforums.org/search.php?do=process&query=ext4)



*UKeywords: 649167 2009 june ext4 links*

---

### Post by master_kernel on 2009-06-21
I have ext4, and the only issue I have is sometimes when I suspend, waking the computer back up results in a I/O error and I lose everything I had open.

So it's simple: don't use suspend :)

---

### Post by blueridgedog on 2009-06-21
> **lovinglinux said:**
> Don't get me wrong, but do we really need another thread about this?



Well, I recall the same discussion when ext3 came out, so I guess it has to run the course.

---

