---
title: "Hour problem"
date: 2008-12-17
forum: General Help
---

### Post by primolarry on 2008-12-17
Hi there,

I formatted my laptop couple of weeks ago, and since then I am having a weird problem with the system time.

When I start my laptop, the hour is always one hour later than it should. If I have internet connection, after some seconds it corrects itself. If I don't have internet connection, if stays wrong. 

The location is correct (Europe,Madrid) and the configuration is set to manual.I've tried setting it to "Internet Synchronized" but the same error happens.My ubuntu version is 8.04.

Any help would be really appreciated.

Regards,

---

### Post by SuperSonic4 on 2008-12-17
Have you checked for DST or something similar? Also, what time does it say in BIOS?

---

### Post by Ayuthia on 2008-12-17
You might want to check /etc/default/rcS and make sure that UTC is not set to yes.  It sounds like the system thinks that your system clock is set to match the UTC which means that you will be one hour off.

---

### Post by primolarry on 2008-12-17
Ayuthia you were right, it was set to UTC. I disabled it and it works perfectly now.

Thanks a lot.

---

