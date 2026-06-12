---
title: "ADCP error with translated japanese games"
date: 2007-11-22
forum: Gaming &amp; Leisure
---

### Post by nekosama on 2007-11-22
just so everyone knows, the game i'm trying to run in wine is Pretty Soldier Wars AD 2048 and the error message that comes up is:

There will be no voice or sound effects because the system does not support ADPCM files. Do you wish to continue? (CODE = 0:0)

clicking "yes" causes wine to close.  i did find another thread with the exact same problem (although the OP never said which game they were trying to run) but his problem was never solved and there wasn't any really useful information.  i searched the net for a bit and while i haven't fixed it i did get more info which may help.

this is a common error when trying to run japanese games which have been translated and published in english, most notably games published by G-Collections, on windows xp.  the cause seems to be with 2 files that were updated with xp:  imaadp32.acm and msadp32.acm located in /windows/system32 .  the new files are version 5.1.xxxx, but many of these games require 5.0.xxxx (which was from windows 2000).  ive searched for hours but the only version i can find for download is 4.0.xxxx (windows 95/98 ).  i replaced the files that came with wine with the 4.0.xxxx (after backing them up of course) but still got the same error message.  if anyone knows where i can download the 5.0 files (or if anyone has them and is willing to upload them somewhere) i would be very grateful. 

of course it's still possible that even with the correct files wine wont be able to run it.  it may be important to note that in windows any time this error message pops up, clicking "yes" will run the game normally, just without voice or sound effects whereas in wine it will not run at all.

---

### Post by aLiase on 2007-12-03
hi,

just wondering if you got a solution yet, I'm also having the same error.

---

