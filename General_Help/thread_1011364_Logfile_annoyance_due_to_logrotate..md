---
title: "Logfile annoyance due to logrotate."
date: 2008-12-14
forum: General Help
---

### Post by albinootje on 2008-12-14
Since years i'm used to typing things like : tail -f /var/log/syslog

However, since a while logging seems to jump from either /var/log/syslog to /var/log/syslog.0 and sometimes it's back to /var/log/syslog.
(After a reboot or a restart of a VE in OpenVZ logging is back to /var/log/syslog)

I've seen this behavior in Ubuntu Hardy and Debian Etch on various installations, and it sometimes drives me crazy, 
seeing nothing with tail -f /var/log/syslog and having to do ctl-c and then up arrow and then add the dot 0 in the end, and press enter again.

I assume it's some bug in logrotate or the logging daemon, but can someone explain why this is happening and whether it's a bug or a "feature" ?

---

