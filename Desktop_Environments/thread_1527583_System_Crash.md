---
title: "System Crash??"
date: 2010-07-09
forum: Desktop Environments
---

### Post by rdunnion on 2010-07-09
Hi For the second day in a row I've come home to a powered off PC. I'm running 64-bit Lucid. I checked syslog and this is what I see:
> Jul  9 12:17:01 ryan-desktop CRON[3112]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  9 12:39:01 ryan-desktop CRON[3123]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul  9 13:16:04 ryan-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Absolutely nothing until I booted up at 13:16. I am still a novice at checking logs but last night I pulled the plug, powered down with the power button, and shutdown with the menu option and they all produced:
> Jul  8 21:42:14 ryan-desktop AptDaemon: INFO: Shutdown was requested
I double checked my power settings and sleep is turned off. Why is this happening?
EDIT: Or better yet, where do I look to find out what happened?

---

