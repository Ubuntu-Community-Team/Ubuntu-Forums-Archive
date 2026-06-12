---
title: "mdadm raid5 array is broken, but cannot determine how..."
date: 2009-01-25
forum: General Help
---

### Post by jspeton on 2009-01-25
I have a 6 x 250GB mdadm raid5 array I originally built on 6.06 server and have, over time, upgraded to 8.10 desktop.

The array has always worked fine, until recently.  Noticing some irregularities after moving files around I started to md5sum the source and destinations and noticed they were often different!  Not good.  In fact I can md5sum the same large file on the array and most of the time I get different results.

mdadm claims all drives are operational.  smartctl, after performing long tests on all drives, claims all drives are healthy.  I've run badblocks (read-only) multiple passes on all 6 drives and they always come up clean.  I've run badblocks on the array itself (read-only) and it comes up clean.  I'm hesitant to run a non-destructive scan because of the possibility that it will completely hose the data.

I've ordered a backup drive to move all the files to pending a catastrophic failure, but if it's just one drive that's failing I'd rather replace the faulty drive, but for the life of me the array appears 100% fine until I mount it, at which point reads become inconsistent.

Anyone have any advice on further checks I can run to determine what's gone wrong??

Thanks!

---

### Post by jspeton on 2009-01-29
Can no one offer any suggestions on how I might isolate the problem?  I have my new drive and am "backing up" what's there but I know what's being copied is not 100% what I started with.

Should I try reassembling the array?  Take out a drive and let it rebuild?  Try a non-destructive write badblocks test on the array?

Help!

:-)

---

