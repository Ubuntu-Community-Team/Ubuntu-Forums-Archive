---
title: "startup log"
date: 2004-12-23
forum: Desktop Environments
---

### Post by pavkonti on 2004-12-23
Where can I find the startup log, because I am receiving two (hotplug) errors?

---

### Post by astoltz on 2004-12-23
[QUOTE=pavkonti]Where can I find the startup log, because I am receiving two (hotplug) errors?[/QUOTE]
 That'd be the command "dmesg".  There's also /var/log/syslog.

---

### Post by Rancoras on 2004-12-23
[QUOTE=pavkonti]Where can I find the startup log, because I am receiving two (hotplug) errors?[/QUOTE]

Their related to pciehp and shpchp aren't they?  If so, look at:

[http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

That should help.  They don't cause problems and they are merely an annoyance.  That page will show you how to keep them from annoying.

---

