---
title: "cron did not worked"
date: 2010-07-07
forum: Desktop Environments
---

### Post by tapas_mishra on 2010-07-07
I scheduled a simple script to run vlc at some time in crontab but it did not run at the specified time

crontab -e
```

 04 8   * * * /home/user/alarm.sh 

```

where as if I run the script manually as root 
```

VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root first and
cannot be run by non-trusted users first).


```

In case if I am logged in as normal user then the script runs properly
```

/home/user/alarm.sh

```

---

