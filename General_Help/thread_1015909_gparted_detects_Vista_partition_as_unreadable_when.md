---
title: "gparted detects Vista partition as unreadable when unmounted"
date: 2008-12-19
forum: General Help
---

### Post by dorkdork777 on 2008-12-19
I'm trying to move some partitions around before I install Ubuntu on my new machine with 2 hard drives ([see here]("http://ubuntuforums.org/showthread.php?t=1015241")). However, when I load up gparted in the Ubuntu 8.10 64-bit LiveCD, my 450 GB Vista partition is detected as unreadable, saying I should run chkdsk /f on Windows. Which I have done - no problems detected. However, the partition is detected perfectly if it's mounted - unmounting it makes it unreadable again, so I can't do anything with it.

This has me stumped. Any help? :)

---

### Post by ajgreeny on 2008-12-19
You are aware, I hope, that you can not do anything to a partition, move it, delete it, resize it, or anything else with gparted, if it is mounted.  It must be unmounted to do anything, and when it's unmounted you can not "read" it.

Or perhaps I have misunderstood your problem.

---

### Post by dorkdork777 on 2008-12-19
Sorry, I suppose I wasn't clear. When it's mounted, I can't do anything with it, as expected, but it does appear properly and I can see how much of it is used. When it isn't mounted, there's a little warning sign next to it, and I can't see how much is used and how much is free, so I'm afraid to do anything with it, in fear Vista might be erased.

Right clicking it and selecting 'properties' results in a window telling me there's problems with 'clusters', whatever those are, and to run chkdsk /f on Windows, which I've done, and it reports no problems. I'm defragging on Vista at the moment, which is taking unusually long for a fresh OEM install... I guess it's because I've removed so much bloatware and trialware :P When it's done I'll post screenshots.

EDIT: [Found a faster way to defrag]("http://www.vistarewired.com/2007/02/15/defragment#skip"), hopefully this should speed things up a bit :)

EDIT 2: Done! Now for the screenshots, hang on...

EDIT 3: Actually, that seems to have fixed it :D trying to resize now...

---

### Post by ajgreeny on 2008-12-19
Good old MS and its need for defragging often!!

---

