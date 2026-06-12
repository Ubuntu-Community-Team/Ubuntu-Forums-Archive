---
title: "unable to edit clock timezone"
date: 2006-09-12
forum: Desktop Environments
---

### Post by deneich on 2006-09-12
call me stupid. I was trying to add software and foolishly removed files from /usr/share/zoneinfo. now - obviously - it is impossible to set the clock to anything but UTC. When entering sudo time-admin in a terminal, the response is:
dennis1@dennis1-desktop:~$ sudo time-admin
Password:

** (time-admin:6637): WARNING **: Could not open */usr/share/zoneinfo/zone.tab*


** ERROR **: Unable to load system timezone database.
aborting...
dennis1@dennis1-desktop:~$

What must one do to reinstall the proper files into /usr/share/timeinfo ?
I have already reinstalled LIBC6 with no success...help.

---

### Post by LotsOfPhil on 2006-09-12
Have you tried:

sudo touch /usr/share/zoneinfo/zone.tab

?

---

### Post by deneich on 2006-09-12
Thanks, I used the TOUCH command. the problem is mostly solved. I can now - at least - manually set my time, however, attempting to change time zones still causes time-admin to crash. Going to try re-adding geographic directories from evolution into /usr/share/zoneinfo and see what happens...wish me luck.;)

---

### Post by deneich on 2006-09-12
Well, no luck. Apparently, /usr/share/zoneinfo is a bit different than /usr/share/evolution-data-server-.16/zoneinfo or /usr/share/apps/libical/zoneinfo. Anybody have any suggestions.

---

### Post by LotsOfPhil on 2006-09-13
> **deneich said:**
> Thanks, I used the TOUCH command. the problem is mostly solved. I can now - at least - manually set my time, however, attempting to change time zones still causes time-admin to crash. Going to try re-adding geographic directories from evolution into /usr/share/zoneinfo and see what happens...wish me luck.;)

What errors are you getting now? Does the time-admin just hang?

---

