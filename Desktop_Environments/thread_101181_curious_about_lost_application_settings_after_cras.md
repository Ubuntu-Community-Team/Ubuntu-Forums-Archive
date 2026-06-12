---
title: "curious about lost application settings after crash"
date: 2005-12-09
forum: Desktop Environments
---

### Post by stanwebber on 2005-12-09
my system locked up this morning (nautilus suspected culprit) & i was forced to reboot.  i run ubuntu on a non-journaling ext2 partition to allow noflushd to spin down my hdd.  on startup fsck ran as per normal, successfully fixed misc filesystem errors & rebooted into ubuntu normally.  i've been thru this scenario countless times before:  everything was ok so long as fsck was able to automatically complete & reboot; if i was instructed to run fsck manually then i knew for sure i was in for some data loss (time to decipher the contents of lost+found to figure out what got borked).

to my astonishment after fsck's successful run & reboot i login to find evolution (running at the time of the crash) has lost all my mail & account settings.  i check lost+found looking for some answers only to find it completely empty.  this is unprecedented in my experience with linux.  i've lost data on numerous occassions before, but never without some trace of evidence pointing to a some possible cause.  i'm curious to know what the hell might have happened.  linux has always performed flawlessly for me, whereas windows has always been wanting & i'd expect this sort of thing everyday of the week.  have i just been lucky with linux so far?

---

