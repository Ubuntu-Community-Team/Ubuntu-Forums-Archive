---
title: "How do we enable LXDE Desktop/LXDE Panel Error logging"
date: 2016-01-04
forum: Desktop Environments
---

### Post by meltingpot2015 on 2016-01-04
Running Ubuntu 14.04.3 LTS Trusty. The lxde desktop panel taskbar keeps restarting now and then without word or warning.

Checked /var/log/syslog but no relevant error messages or warnings there. Also looked at  the log files ~/.xsession-errors
and ~/.xsession-errors.old. 

.xsession-errors has the following:
```
Script for ibus started at run_im.
```

.xsession-errors.old has:
```
Script for ibus started at run_im.
init: lxsession main process (1863) terminated with status 1
init: Disconnected from notified D-Bus bus
```

Both files have a timestamp from about 24 hours ago. However, LXpanel taskbar restarted unexpectedly about 2 hours ago. I don't receive any prompt to report the problem or anything like it.

---

