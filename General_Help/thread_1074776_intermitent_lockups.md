---
title: "intermitent lockups"
date: 2009-02-19
forum: General Help
---

### Post by chris.rickey on 2009-02-19
I have been using Intrepid 64bit for about 2 weeks now as a XP replacement box.  I still have to run XP for work, so I do it in a vmware.

I have had my laptop lock up on me a few times.  In fact it happened about 4 times this morning.  I think I finally narrowed it down to the cause.  It only seems to happen when I am doing some large file operations.  This morning I was attempting to copy a large (600MB) file from my desktop to my NAS.  I have mapped to the NAS via a windows share.  The whole machine locks and the caps lock and num lock lights start flashing.  Gotta power cycle at that point.

I tried some other things, specifically I saw a thread possibly putting the blame on the nvidia drivers, so I tried using the 173, 177, and 180 builds, but got lock ups with all three.  It finally occurred to me that it only happens when copying files to the NAS.  I havent' done it in the last 6 hours and so far no issues.

Anyone know if my assumptions are correct, and how I might verify them?

---

