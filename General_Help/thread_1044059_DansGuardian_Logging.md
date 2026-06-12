---
title: "DansGuardian Logging"
date: 2009-01-19
forum: General Help
---

### Post by dm993 on 2009-01-19
Is there a way of explicitly telling DansGuardian to rotate its log files at a specified time?

the access.log logfiles stored in /var/log/dansguardian rotate fine everyday but never at an exact time.

I'd like to be specific about it because I'm copying the contents of the previous full days log (access.log.1) to a samba share and I want to know the rotation has occured before crontab executes the script to copy the previous days logfile (access.log.1)

I've searched through dansguardian.conf and also DansGuardian's website but can't find an answer.

---

