---
title: "Linux FileSystems"
date: 2005-11-02
forum: Desktop Environments
---

### Post by NewWithoutClue on 2005-11-02
Question: What FS is 'the best'?

*note: google could be a quick answer, but for me and others who use this forum, it would be great info.*


w00t,
Paul.

---

### Post by jatos on 2005-11-02
Ext3 is pretty good but the one I think is best and always use is reiserfs, it does seem more advanced to me. Whatever FS you use make sure its a journalling FS as I have seen a lot more cases of people been able to recover journalling FS's when they cock things up.

---

### Post by dave9191 on 2005-11-02
I don't think there is such a thing as a "best" FS. Each have their own mertis and shortfalls. Ext3 and ResierFS are both extremly good. I've been using the latter for a few months now and I'm really happy with it. 

Dave

---

### Post by NewWithoutClue on 2005-11-02
Thank you for the for your input. ( both of you )

Paul.

---

### Post by magnusbb on 2005-11-02
I agree. Both ext3 and ReiserFS are decent, journaling file systems. I have recently switched from ReiserFS (which I've used for many years) to ext3, due to a partition corruption that made me a bit angry. 

Some people say that ext3 is more reliable than ReiserFS, while ReiserFS supporters claim their FS to be faster than ext3 for the typical desktop user. But generally, you'll like them both, I think.

---

### Post by dave9191 on 2005-11-03
Ext3 has been around longer and is a proven as a FS.
Ext3 is very reliable. 
Ext3 needs to be scanned every 30 mounts.  

Reiser FS is better at dealing with lots of small or large files. 
ReiserFS doesnt have a the fschk scan every 30 mounts.
ReiserFS recovers from errors very quickly.
ReiserFS has okish performance for your avarage files (as opposed to lots of small and large). 

Dave

---

### Post by slux on 2005-11-03
I've been using them all, there are also JFS and XFS, the latter being SGI's answer and apparently good when dealing with huge files while JFS is IBM's filesystem that's been ported over from OS/2 and also exists on AIX.

Looking at the benchmarks, ext3 is pretty much always the slowest one but it boasts backwards-compatibility and is dependable which I guess is why most distributions use it.

I've had my filesystem corrupted on ReiserFS and ext2 (might've been ext3, that was too long ago) but I think there may have been contributing factors when that happened. I pretty much trust all of them and while I've only been using JFS and XFS for a year or two now, I've had zero problems with either one.

Personally I find it a bit sad that so many distros opt for ext3 when it's clearly not the best option performance-wise. Reiser4 is also going to be interesting when it becomes stable...

---

### Post by jonny on 2005-11-03
Take a look at this table of comparisons on [Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_file_systems").  It's interesting that the official MythTV documentation recommends XFS or JFS due to their efficiency at creating and deleting very large files.

I'm using JFS for that reason, but it's not terribly well integrated.  Some utility and partitioning programs (eg gParted) don't know what it is and can't give any information about disc utilisation on the JFS partition.

---

### Post by bionnaki on 2005-11-03
I use reiserfs.
personally, I cannot tell the difference between that & ext3.
my desktop habits include email, browsing, downloading music illegally, IM, and watching porn.

---

### Post by NewWithoutClue on 2005-11-03
Thanks all for the answers. Something more for me to know, thanks to you people.

Paul.

---

