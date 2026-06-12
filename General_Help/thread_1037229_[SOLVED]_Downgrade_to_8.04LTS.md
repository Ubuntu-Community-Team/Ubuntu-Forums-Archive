---
title: "[SOLVED] Downgrade to 8.04LTS ??"
date: 2009-01-11
forum: General Help
---

### Post by hawkhock on 2009-01-11
Graphics card no longer supported; 173 driver not compatible with 8.10. Haven't found any way to make it work.  Plan to downgrade from 8,10 to 8.04 for graphics card compatibility.  Basic user, no bells & whistles, using 8.04 should be fine for me.  Hard drive is partitioned for /ext3, /home, /swap.  

If I understand correctly, I should be able to install 8.04 on /ext3 and all files on /home should be recognized. Will back up /home before install as safety factor.

? Are there any problems I should be aware of in advance? 
? Are most packages available to 8.10 compatible with 8.04?

Any advice would be appreciated.

---

### Post by adult swim on 2009-01-11
whenever you install again, when you get to the partitioning section choose manual. make sure and select your old / and make its mountpoint / you should probably select that one to be formatted.
then go to your old home partition and double click it and choose it to be mounted as /home MAKE SURE NOT TO FORMAT THAT ONE!
after doing those two steps you should be good to go.

---

### Post by hawkhock on 2009-01-11
Thanks for reply.  Will open GPartEd to make sure I know what you are talking about before I attempt anything. Noob - learning as I go.  Will be back to mark as solved or ask more questions!  I've downloaded the ISO file but need to burn a CD and make sure it works first.

---

### Post by hawkhock on 2009-01-11
Thanks again for your help.  I understood your directions when I got to the manual install screen and successfully installed 8.04LTS. Need to get customizing packages finished and then will graphics card compatibility issue.

---

