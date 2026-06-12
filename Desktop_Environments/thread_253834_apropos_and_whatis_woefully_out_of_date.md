---
title: "apropos and whatis woefully out of date"
date: 2006-09-08
forum: Desktop Environments
---

### Post by indigoshift on 2006-09-08
I've installed a lot of programs (I'm running the 6.06 release), and the "apropos" and "whatis" commands are very much out of date.

I'd like to update them, but can't figure out how.  Trying to run "makewhatis" and "dbupdate" result in "command not found" errors.  I figured these commands just weren't installed, but searching for them in Synaptic yields no results--and I have all repositories checked.

Searching for "Makewhatis" and "dbupdate" on the forums here returns no results, so I'm officially stumped.  What am I missing here?

Thanks!

---

### Post by Junx on 2006-09-09
sudo mandb

I guess that's what you're looking for.

---

### Post by funchords on 2006-09-09
Thanks for the question and answer.  I was wondering this myself.

I notice that this catches itself up after a while -- without any user intervention.  

Yesterday, I installed a bunch of the synce stuff, but there weren't any man pages listed for them.  Today, "wallah," the man pages were there.

Is mandb part of some cron job by default?  Anyone know?

*edit: found it ... /etc/cron.daily/man-db *

---

### Post by indigoshift on 2006-09-09
> **Junx said:**
> sudo mandb

I guess that's what you're looking for.

That's it!  Thanks!

---

