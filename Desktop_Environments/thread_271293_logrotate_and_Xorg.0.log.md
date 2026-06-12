---
title: "logrotate and Xorg.0.log"
date: 2006-10-04
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-10-04
today I found that I don't have backlogs for my Xorg.0.log files. I
checked logrotate.conf and it says log files are kept for four weeks. my
Xorg.0.log.old file starts with the latest log and there is no .gz files
of this log.

is this normal behavior? and if so, how do I change it? the man page of logrotate and the googles I bumped into weren't very helpful :) thanks

---

### Post by dcstar on 2006-10-05
> **towsonu2003 said:**
> today I found that I don't have backlogs for my Xorg.0.log files. I
checked logrotate.conf and it says log files are kept for four weeks. my
Xorg.0.log.old file starts with the latest log and there is no .gz files
of this log.

is this normal behavior? and if so, how do I change it? the man page of logrotate and the googles I bumped into weren't very helpful :) thanks

Look in /etc/logrotate.d and you should see how all the others are done, just copy one of those and configure it to your needs.

---

### Post by towsonu2003 on 2006-10-05
> **dcstar said:**
> Look in /etc/logrotate.d and you should see how all the others are done, just copy one of those and configure it to your needs.

thanks for the reply. 

I'll take the acpid and change it, but it restarts the acpid service. do I need to restart a service for the Xorg.0.log file? 

```

/var/log/Xorg.0.log {
    weekly
    rotate 4
    compress
    missingok
    postrotate
        /etc/init.d/**??????** restart >/dev/null
    endscript
}

```

oh, end, is this supposed to be? do you have just the Xorg.0.log.**old** file in your /var/log folder as well (and no .gz files)?

---

