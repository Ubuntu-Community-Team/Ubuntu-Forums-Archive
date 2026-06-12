---
title: "Where is the boot log?"
date: 2009-01-03
forum: General Help
---

### Post by dnoyeb on 2009-01-03
I'm having some issues on startup and shutdown.  I saw some items fail, but I have no idea where to find the log of this failure.  I do not see a boot.log file in /var/log

Where should I look for the boot log?

---

### Post by drs305 on 2009-01-03
The initial stages of boot can be found in /var/log/dmesg .

You can install something like bootchart which can give you more info and a graphical view of the time it takes various processes to load. It's available in synaptic.

---

### Post by dnoyeb on 2009-01-03
Thanks.  Im just looking for a log of the services that start and stop during boot and shutdown.  And if they are successful or not.  I don't need more info like time.  Just the OK/FAIL info.

During boot I see a lost of things with OK next to them and sometimes FAIL next to them.  However, I can't find where this is logged.

---

### Post by sdennie on 2009-01-03
I don't know of a place to see the [OK] or [FAIL] messages.  You'd have to look through /var/log/syslog to find what is not working I think.

---

