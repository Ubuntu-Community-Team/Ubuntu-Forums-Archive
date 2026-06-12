---
title: "Slow Machine issue"
date: 2004-12-03
forum: Desktop Environments
---

### Post by JabberWonkie on 2004-12-03
I just installed Ubuntu and I think it's great except for one thing.  When the GDM starts up the machine gets veerrrry slow (from loading the logon page and beyond).  I check the memory usage it's only using 94 of 512 megs and no swap usage.  Top doesn't show any processes out of control.  I did "hdparm -t /dev/hda" and found that the disk reads were only averaging 6 meg a second. 

The machine is only a year old and I don't think the hard drive is junk.  Also using another distro I was averaging 20 meg a second and when I booted into recovery mode I am averaging 24 megs a second.  I tried some of the options in hdparm to see if that would help (turning on multi sector, chaning bandwidth, etc) no change.

Does any one have any ideas?

Thanks

(and sorry for any possible spelling errors)

---

