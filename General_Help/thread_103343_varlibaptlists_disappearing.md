---
title: "/var/lib/apt/lists disappearing"
date: 2005-12-13
forum: General Help
---

### Post by Rumpty on 2005-12-13
From time to time I am losing all (or almost all) the repository info in var/lib/apt/lists, which means that sudo apt-get update is required to be run. On a dial-up connection this is a bit of a pain if it has to be done very often, which it does. It has just dawned on me that the lists folder is being cleaned out regularly by a cron job. Is that right? There is certainly something in cron.daily to do with apt, but I am not sure exactly what is being done.

---

### Post by outtacontrol on 2006-01-18
Mine is doing the same thing as well, and yes, it is a cron job and like you, I haven't figured out what's causing it to disappear.  Can anybody help with this?

---

### Post by outtacontrol on 2006-02-01
up

---

