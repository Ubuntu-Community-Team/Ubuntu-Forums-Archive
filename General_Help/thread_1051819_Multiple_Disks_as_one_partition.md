---
title: "Multiple Disks as one partition"
date: 2009-01-27
forum: General Help
---

### Post by Die-Walnuss on 2009-01-27
Hello!

I want to combine multiple harddrives to one, just like a raid 0. But if a drive has a failure, only the files on this drive should be lost. It would be nice, if I could add and remove harddrives from this 'pool'.

In addition to that, I'd like to encrypt all the data on the drives.

Does someone have an idea how to realize that?

Thanks in advance!

---

### Post by mb_webguy on 2009-01-27
You should probably have a look a these threads:

[http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by albinootje on 2009-01-27
> **Die-Walnuss said:**
> Hello!

I want to combine multiple harddrives to one, just like a raid 0. But if a drive has a failure, only the files on this drive should be lost. It would be nice, if I could add and remove harddrives from this 'pool'.

Take a look at software Raid5, Raid6 and Raid10.
> 
In addition to that, I'd like to encrypt all the data on the drives.

Raid and disk encryption ? That might be too much to ask for, but perhaps someone else can give a better answer to this.

---

### Post by Die-Walnuss on 2009-01-27
Thank for your answers.

A Raid 0, 1, 01, 5 etc. isn't the right solution for me, because I can't add drives to it without reformatting.

In addition to that, I don't need redundancy.

---

### Post by plucky on 2009-01-27
Could this be what you want?

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

---

### Post by Die-Walnuss on 2009-01-27
> **plucky said:**
> Could this be what you want?

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

Yes, that sounds good. Thank you.

But what happens, if a disk has a failure? Are the files on the other hard drives still available?

---

