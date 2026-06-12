---
title: "Expanding a RAID5 array"
date: 2012-12-04
forum: Desktop Environments
---

### Post by promorphus on 2012-12-04
So, I have a feeling this is a ridiculously easy question to answer, but I'd like to verify prior to potentially ruining a ton of data.  

Currently, I have a 18TB RAID5 array (7x 3TB disks) and I'm trying to add another one. Now, I'm aware that there's a way to do it command line via mdadm without losing data, BUT, what I'm trying to figure out is if I can use the Disk Utility to expand the array without wiping out the data. In particular, I'm selecting the raid array, and then clicking 'Edit Components' and then 'Expand Array' and adding a disk to the array.


Please, in no uncertain terms: If I add a disk to the array in this manner (via the Disk Utility), will it erase my data?

Thanks in advance.

---

### Post by promorphus on 2012-12-05
No love? 

bump

---

### Post by mbarland on 2012-12-06
Is there a reason you want to avoid the command line? I've never worked with mdadm arrays in gparted or the like. 

I added a couple disks to my array and expanded them. This here: [http://ubuntuforums.org/showthread.php?t=517282](http://ubuntuforums.org/showthread.php?t=517282) looks like the tutorial I followed, go to the "Expand Array" section. It is really easy, just takes a long time. Just make sure to backup first in case of a problem.

---

### Post by promorphus on 2012-12-10
> **mbarland said:**
> Is there a reason you want to avoid the command line? I've never worked with mdadm arrays in gparted or the like. 

I added a couple disks to my array and expanded them. This here: [http://ubuntuforums.org/showthread.php?t=517282](http://ubuntuforums.org/showthread.php?t=517282) looks like the tutorial I followed, go to the "Expand Array" section. It is really easy, just takes a long time. Just make sure to backup first in case of a problem.


My issue is, there's really no practical way for me to make a backup, but it's pretty imperative that I grow the array.  At the moment, it's a 18 terrabyte array, so it's pretty impractical for me to make a backup of it (cost effectively anyhow). 

Again, are we sure that growing that array won't erase the data on it?

---

### Post by Cheesemill on 2012-12-11
I've used mdadm to add disks and grow arrays several times without any issues at all.
If you are uncomfortable using the command line for this then my first stop would be to take a look at the excellent mdadm tutorials that rubylaser has written on his website.

[http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)

Check out the article titled 'Adding an extra disk to an mdadm array'.

Although I've never had any problems this doesn't mean that it won't happen. Any sort of operation like this inherently carries an element of risk.

If I was in your situation and running a 7 x 3TB RAID5 with no backup that had important data on it I'd probably be losing sleep over it, there a plenty of ways that you could lose all of your data.
If there is no way for you to backup then obviously your data isn't important to you. RAID arrays do fail, especially the type that you are using. I would recommend at the very least that you migrate your array to a RAID6.

[SIZE=3][COLOR=Red]***RAID is never a substitute for a proper backup strategy.***[/COLOR][/SIZE]
RAID5 is a business continuity solution that only protects you from single drive failure. It doesn't protect against multiple drive failure, hardware failure or user error. You should always have a proper backup strategy in place along side.

---

