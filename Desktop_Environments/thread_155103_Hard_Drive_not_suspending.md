---
title: "Hard Drive not suspending"
date: 2006-04-04
forum: Desktop Environments
---

### Post by noObiE_4_life on 2006-04-04
Using hdparm, my hard drive goes into suspend but immediatly reactivates. Sleep will shut the drive off, it can only be reactivated by a command in the same terminal window. I get annoyed by the harddrive noise when Im not using my machine, though I prefer not to turn the machine off, so I really want to have HD suspend power management working.
Im using: SAMSUNG SV8004H Firmware Revision:  QR100-07

Has anyone else experinced this? Any suggestions what may be bringing the harddrive right back up from suspend? Ive stopped as many non-esential processes as possible, to no avail.

---

### Post by hajk on 2006-04-04
Which filesystem do you use?

ReiserFS is known to generate some disk activity every 5 seconds, so suspending will only work that long (or short). Not sure, but I guess ext3 does something similar.

---

### Post by noObiE_4_life on 2006-04-05
Yes, using LVM, ext3 filesystem. Thanks for the tip, I'll research that, but if it indeed writes that often I suspect my this way to a quiter computer may be a dead end. Well, thin terminal here I come!

---

