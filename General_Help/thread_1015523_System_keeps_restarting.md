---
title: "System keeps restarting"
date: 2008-12-18
forum: General Help
---

### Post by pot_pie on 2008-12-18
I'm running Ubuntu 8.04 as a home server and over the last few days it has started spontaneously rebooting. This is what I'm seeing in the syslog starting about 5-15 mins after startup (the time between these events is very consistent):

Dec 18 18:00:57 server ntpd[5682]: synchronized to 132.246.168.164, stratum 2
Dec 18 18:00:57 server ntpd[5682]: kernel time sync status change 0001
Dec 18 18:16:11 server -- MARK --
Dec 18 18:17:01 server /USR/SBIN/CRON[5686]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 18:36:11 server -- MARK --
Dec 18 18:56:29 server syslogd 1.5.0#1ubuntu1: restart.

I'm a newb with Ubuntu and have no idea what to make of this... Again, it's only started recently and I've made no changes to the system, except for the regular system updates.

Thanks,
Brent

---

