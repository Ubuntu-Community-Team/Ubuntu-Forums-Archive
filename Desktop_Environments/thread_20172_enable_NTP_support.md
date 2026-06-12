---
title: "enable NTP support"
date: 2005-03-15
forum: Desktop Environments
---

### Post by couda on 2005-03-15
No doubt a simple question - I'm trying to get Ubuntu (warty) to synchronize the clock with a time server. Checking the box in Time and Date settings pops up an alert telling me to enable Network Time Protocol (NTP) support. How..? Where..?

Cheers, Couda

---

### Post by alastair on 2005-03-15
It's probably only wanting the startup initscript :

/etc/init.d/ntpdate

to run (package ntpdate).

To make sure it runs at boot, you need to set up the links in the runlevel directory. 

Perhaps read :

man update-rc.d

Alternatively, see "man ntpdate" and make a cron job?

---

