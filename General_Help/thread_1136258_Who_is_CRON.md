---
title: "Who is CRON?"
date: 2009-04-24
forum: General Help
---

### Post by Miles_Prower on 2009-04-24
```
Apr 24 20:17:01 tornado CRON[9426]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 24 20:17:02 tornado CRON[9426]: pam_unix(cron:session): session closed for user root
taels@tornado:/var/log$ man grep
taels@tornado:/var/log$ grep -c CRON auth.log
234
```


ACK! CRON is some kind of bus, right? Wait, no it's an automated process. How, though, is it opening sessions for the user root? I thought ubuntu had root disabled by default....

---

### Post by Rocket2DMn on 2009-04-24
cron is a process that is used for scheduling.  It does some stuff automatically, but users can also configure it to do things at specfic times or intervals.
See [uhelp]community/CronHowto[/uhelp] for more info.

---

