---
title: "Dell Broadcom Kernal Panic no boot - one solution"
date: 2012-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by FrankTyro on 2012-05-28
Decided I was going to put Xubuntu on my Dell Inspiron B130 Celeron 1.4 ghz 1.5 gb ram. Downloaded, burned cd, froze when doing live boot.  Tried again, no luck. Finally used alternate cd, direct install.  Seemed to go ok, but when I went to boot, it froze with message about some bcm43 wireless files not present, and would go no further.  (won't even start without wireless? Not very user friendly.)  So I removed the wifi card, and it booted just fine.  Nothing on your forum, but the Linux Mint forum had advise about the Linux 3 kernal would panic if the broadcom wifi drivers were not installed.  Tried their remedies, install firmware-b43 - no go; installed ndswrapper  with xp driver- no go.  Apparently if the card isn't present, these will not actually install.   Finally, after digging around in synaptic package manager, I installed both the firmware-addon-dell and linux-firmware-nonfree.  Put the card back in and bingo - the OS finally booted. and wifi works.  Good luck to you!

---

### Post by mikewhatever on 2012-05-28
If you want anyone to benefit from the above, it's probably a good idea to post the model of the wireless card that caused kernel panic. Apparently, not all of them do, as, obviously, scores and scores of users have not had that kind of problem.
How do you know it was kernel panic, by the way?

...and good luck to you too.

---

