---
title: "Best filesystem type"
date: 2006-08-02
forum: Desktop Environments
---

### Post by nanophobic on 2006-08-02
This one time dapper froze on me and I had to force shutdown. As a result a sector of my harddrive got bad. To the best of my efforts, I haven't been able to repair that portion of my hard-drive. 

I used ext3 filesystem. What I want to know is, which filesystem type is best suited to handle improper shutdowns? 

Moreover, what else can I do to prevent any such damage to the new hard-drive that I have just ordered. 


thanks in advance

---

### Post by Ramses de Norre on 2006-08-02
You mean a physically bad block or just data corruption? If it's physical damage you can't blame the file system, it's the hard disk getting old then.
Data corruption can occur but journalling should prevent this, this doesn't work perfect all the time though, I've been allread forced to reinstall due to data corruption after improper shutdowns..

---

### Post by reclusivemonkey on 2006-08-02
> **nanophobic said:**
> This one time dapper froze on me and I had to force shutdown. As a result a sector of my harddrive got bad. To the best of my efforts, I haven't been able to repair that portion of my hard-drive.

Can you tell us what steps you took to repair the bad sector? A friend of mine for whom I built a PC many years back had her first problem when she turned off the PC without letting it shut down. It was formatted reiserfs, and it was fairly simple to fix the problem. You can also get utilities from hard drive manufacturers in the form of live disks which can repair the damage (I used one of these from Seagate for one of my drives; although it didn't fix the problem the drive was still under warranty).

---

### Post by mchatel on 2006-08-02
To go back to the original question...  "Which filesystem type is best suited to handle improper shutdowns?"

Any of the journaling file systems, are best to handle this type of situation, in the future.  This includes ext3.  Other popular journaling fileystems for Linux are ReiserFS (I use this one, I like it), XFS, and JFS.  They all have their slight advantages/disadvantages.  Some are better to use on monstrously big disks, some are better to use with multiple smaller files, etc.

Chances are, the problem you had with your ext3 filesystem data... probably would have still happened with any of the other journaling systems too.  Probably more hardware related.  They are good, but they can't be 100% foolproof in every improper shutdown situation.  Much superior to non-journaling filesystems though.

---

### Post by nanophobic on 2006-08-02
> **Ramses de Norre said:**
> You mean a physically bad block or just data corruption? If it's physical damage you can't blame the file system, it's the hard disk getting old then.
Data corruption can occur but journalling should prevent this, this doesn't work perfect all the time though, I've been allread forced to reinstall due to data corruption after improper shutdowns..

While booting I get a series of "Buffer I/O error on device ..." and then it goes to root prompt telling me to run fsck manually. Running fsck manually produces the same errors.

This happened even after fresh format. So I guessed the hard drive must have gone bad.

But my concern is, what if dapper freezes again and I do an improper shutdown and my new hard drive gets junked again :(

---

