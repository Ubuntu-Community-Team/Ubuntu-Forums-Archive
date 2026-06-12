---
title: "Where is the output from my init.d script?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by loonsailor on 2006-07-03
I've written my first init.d script, loosely based on init.d/skeleton.  I know that it's run, because the process is up, but I can't find the script output anywhere.  It has several echo's in it.  I've grepped for the expected output in /var/log/*, and in the dmesg output, but no luck.  Where can I see these?  Also, if the process generates any errors during operation, where would I see those?  Basically, what is stdout and stderr set to for a script run by rc.d, and for the process spawned by that script?

I'm running 6.06 desktop.

Thanks much for any help.

---

