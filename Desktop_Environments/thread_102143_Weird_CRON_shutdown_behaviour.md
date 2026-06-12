---
title: "Weird CRON shutdown behaviour"
date: 2005-12-11
forum: Desktop Environments
---

### Post by bored2k on 2005-12-11
I've been noticing for a while (even on fresh installs) that for some unknown reason my computer shuts itself off on Sundays, and although the hour this happens is different, it always happens on the 17th minute... **always.** When I check the logs, it always says
```
(pam_unix) session closed for user root [Process CRON[7797]).
```

What the **heck** would you people presume is happening?!

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=bored2k]I've been noticing for a while (even on fresh installs) that for some unknown reason my computer shuts itself off on Sundays, and although the hour this happens is different, it always happens on the 17th minute... **always.** When I check the logs, it always says
```
(pam_unix) session closed for user root [Process CRON[7797]).
```

What the **heck** would you people presume is happening?![/QUOTE]
Is one of your cron scripts under /etc/cron.weekly shutting down the PC explicitly?

---

### Post by bored2k on 2005-12-11
[QUOTE=cwaldbieser]Is one of your cron scripts under /etc/cron.weekly shutting down the PC explicitly?[/QUOTE]
```
/etc/cron.weekly$ ls
0anacron  cvs  man-db  popularity-contest  sysklogd
```

The only cron script that would shut down my box that I know of resides in my crontab, which is:
```
 crontab -l
20 6 * * 1,2,3,4,5      sudo /sbin/shutdown -h now
```

---

