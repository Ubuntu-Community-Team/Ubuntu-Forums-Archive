---
title: "Cron scheduled shutdown when suspended"
date: 2016-07-31
forum: Desktop Environments
---

### Post by shakerb on 2016-07-31
I am a newbie to Ubuntu/Linux, and to this forum, so forgive me if this post annoys anyone.

I am trying to schedule shutdown of the system (an old Dell Inspiron Zino-HD, running on Xubntutu 16.04.1) everyday at 11pm. Here's my (sudo/root) crontab entry:

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
00 23 * * * shutdown -P now

```

The system is shutdown at the scheduled time and the power is off, if it is active. My problem is this: I have power-saving settings to suspend the system if inactive for 30 minutes. When the system is suspended the cron job fails to shut it down. I have even tried ```
... poweroff -f
``` with no luck. If I wake up the system, cron kicks in and and shuts the system down. Is this normal behavior? If so, is there any way to programmatically shut the system down when it is suspended?

Thank you for your attention and help.

---

