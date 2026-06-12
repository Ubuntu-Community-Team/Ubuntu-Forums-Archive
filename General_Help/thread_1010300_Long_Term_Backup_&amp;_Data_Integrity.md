---
title: "Long Term Backup &amp; Data Integrity"
date: 2008-12-13
forum: General Help
---

### Post by chrispoole on 2008-12-13
So, you implement your long-term backup solution any way you want.

You might backup to two hard drives, then copy the data to new drives every few years.

But how do you ensure the data is the same?

(Assuming you don't use ZFS or store everything in git or some database, how do you compare the integrity of files on the system between drives?)

Is there a program that'll go through and SHA1 everything, reporting the files that don't match?

---

### Post by tigerstripedcat on 2008-12-13
I don't think 99% of people on here need to do what you need to, or if they do they just don't care about data that old, so you might need to wait or actively seek out some enterprise-level IT people (and probably at a university).  

Are you trying to ensure a valid copy or ensure no general corruption at all?  If the later, you can't just store these disks, you have to constantly run some kind of script that does a checksum across several drives (you'll probably have to google for that), as data will become corrupted even in storage.  You can calculate the probability of a given bit flipping over N number of drives, and find out what is viable for you. If you need to keep this data for 200 years, you'd probably be better of not asking someone on ubuntuforums ;).  If you only need it for 10 years, then making a copies of multiple copies on durable media in proper storage every two years should be fine.  (The probability of total failure in that case wouldn't even show up on your calculator.)

But then again I could be completely wrong about all this. ;)
TSC

---

