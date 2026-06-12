---
title: "Edubuntu 8.10 boot error"
date: 2009-02-23
forum: General Help
---

### Post by wangsuda on 2009-02-23
When I boot up my computer, I receive the following error message:

PROCESS 1939: CANNOT PARSE CONFIG FILES. COULD NOT OPEN CONFIG FILES. NOTHING TO DO **BYE**

Any idea what this means or how to fix it? My computer does boot and everything seems to work ok, just worried that this might cause a problem in the near future.

---

### Post by lykwydchykyn on 2009-02-24
Sounds like some unconfigured service trying to start at boot. You might try looking through /var/log/syslog or the output of dmesg to see if you can identify what service it might be.

---

