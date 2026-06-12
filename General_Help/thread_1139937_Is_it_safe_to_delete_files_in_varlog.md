---
title: "Is it safe to delete files in /var/log?"
date: 2009-04-27
forum: General Help
---

### Post by davideotape on 2009-04-27
The question says it all really. I have over 2GB of files in my /var/log, so I am wondering if they are safe to delete.

All help appreciated :D

David

---

### Post by jimbob on 2009-04-27
I believe it is, those are merely previous days archives.

Probably don't delete the current day, although the system will quietly recreate them if you do.

---

### Post by davideotape on 2009-04-27
Thanks, I've safely just freed up over a GB of space. :D

---

### Post by jimbob on 2009-04-27
That's for today only.

  Keep in mind that they will fill up again over the next few days.

You can change the number of days that are stored if you like but I would have to do some research to tell you exactly how.

---

### Post by sisco311 on 2009-04-27
logrotate  is  designed to ease administration of systems that generate
       large numbers of log files.  It allows automatic rotation, compression,
       removal, and mailing of log files.  Each log file may be handled daily,
       weekly, monthly, or when it grows too large.

For details, read the man page:
```
man logrotate
```

---

