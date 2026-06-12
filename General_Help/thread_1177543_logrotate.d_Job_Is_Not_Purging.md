---
title: "logrotate.d Job Is Not Purging"
date: 2009-06-03
forum: General Help
---

### Post by cleanden on 2009-06-03
I tried setting up a logrotate job as follows:

```
nano -w /etc/logrotate.d/assp

/usr/share/assp/logs/*.maillog.txt {
        daily
        missingok
        rotate 4
        compress
        notifempty
        create 755 nobody nogroup
}
```

with the intention of compressing log files on a daily basis, keeping only 4 archives available at any given time.

However, 2 months later I see 8 zero-byte *maillog.txt files and 8 corresponding .gz files

I found mention of maybe needing to run:

```
sudo logrotate -f /etc/logrotate.conf
```

but after running that and waiting a day, things are no different
Can someone help point out what I'm not doing right?

Thanks

---

