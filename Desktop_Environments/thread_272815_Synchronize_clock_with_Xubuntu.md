---
title: "Synchronize clock with Xubuntu?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by kikinovak on 2006-10-07
Hi,

I'm running Xubuntu 6.06, and I wonder how I might synchronize my clock. I've been using Ubuntu 6.06 for a short time before, and it was just a matter of right-clicking on the clock, open the clock configuration window, and then click on "Synchronize now". By the way, I can't really use periodic synchronization, since I'm on dialup here.

Anyone knows what's the command under the hood for doing that?

---

### Post by jpkotta on 2006-10-07
I put this in a script in /etc/cron.weekly.  You can of course do ```
sudo /etc/cron.weekly/ntpdate
``` to sync on demand.

```
#!/bin/sh

if [ -r /etc/default/ntpdate ] ; then
    . /etc/default/ntpdate
    /usr/sbin/ntpdate $NTPOPTIONS $NTPSERVERS
else
    /usr/sbin/ntpdate -u -v ntp.ubuntu.com
fi

```

---

### Post by jpkotta on 2006-10-07
Also, [https://help.ubuntu.com/community/NTPTimeSynchronisation](https://help.ubuntu.com/community/NTPTimeSynchronisation)

---

