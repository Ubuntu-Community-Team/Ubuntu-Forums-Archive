---
title: "Upgraded breezy to dapper now freezing"
date: 2006-09-16
forum: Desktop Environments
---

### Post by mistajon on 2006-09-16
Hi all

Very frustrating! What can I post to debug this annoying problem? Every 15-20 mins ubuntu freezes.  I can move mouse but do nothing else ie no ctrl alt backspace - anything.  Also disk manager keeps mounting my ntfs drives, is there a way to stop it? I edited mtab and they went away until I reboot they are back.  Probably not a big issue, most of all want to fix the freezing.

This is what happens:  Note the nvrm xid error that was when it crashed.

Sep 17 09:43:40 localhost kernel: [17179878.660000] NTFS volume version 3.1.
Sep 17 09:50:23 localhost kernel: [17180281.592000] NVRM: Xid (0001:00): 13, 0000 01013900 00000039 00000314 00efebe7 00000002
Sep 17 09:51:51 localhost kernel: Inspecting /boot/System.map-2.6.15-26-386
Sep 17 09:51:51 localhost kernel: Loaded 23037 symbols from /boot/System.map-2.6.15-26-386.
Sep 17 09:51:51 localhost kernel: Symbols match kernel version 2.6.15.
Sep 17 09:51:51 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Sep 17 09:51:51 localhost kernel: [17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006

edit-
crashed again

Sep 17 10:08:35 localhost kernel: [17180599.860000] NVRM: Xid (0001:00): 13, 0000 01013900 00000039 00000328 00000000 00000100

edit-
I have discovered if I leave my pc running for over half hour with screensaver kicks in etc everything still works does not lock up.  Only appears to happen when I'm doing something like surfing firefox or watching a dvd etc. Any ideas?
Cheers
Jon

---

### Post by mistajon on 2006-09-16
I have narrowed it down to Firefox.  Any ideas ?

---

