---
title: "System Freezes When Trying to Burn Data CD"
date: 2005-07-14
forum: Desktop Environments
---

### Post by tstrickland on 2005-07-14
When I attempted to burn two small files to a CD with K3b, my system froze up and I had to reboot. I burned these same two files to a DVD without problems. 

I submitted a detailed bug report to K3b, and in response, I was told that: 

1). This wasn't a system freeze (It sure fooled me!).

2). It isn't a K3b bug. 

3). It is most likely that cdrecord is blocked by automounting.

I was advised to disable automoting [sic] for now. ](*,) 

Two questions:

1. Does one need to be a Linux expert to  use K3b?

2. Is there another Linux program that will burn CDs, etc?

Thank you.

---

### Post by flying_icarus on 2005-07-14
To try and answer your questions...

1) You should definitely *not* have to be a Linux expert to use K3B, it should be the most user friendly burning application for Linux ;)

2) You could try X-CDroast or maybe GCombust (gnome based, not too sure if it's even the right tool for the job)... or progresing to even less user friendly command line tools, cdrecord and mkisofs :)

And as to why the freeze... have you tried playing with hdparm settings? Maybe there is an issue with some combination of motherboard, cd recorder and DMA/PIO settings?

---

