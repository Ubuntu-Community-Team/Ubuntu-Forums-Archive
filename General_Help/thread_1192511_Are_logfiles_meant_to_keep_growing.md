---
title: "Are logfiles meant to keep growing ?"
date: 2009-06-20
forum: General Help
---

### Post by jacktar on 2009-06-20
Certain log files on my system such as syslog and kern.log are growing quite large. Every time I reboot they get bigger. Do they have to be deleted manually or do they ever get erased ?

---

### Post by Gunman1982 on 2009-06-20
What do you mean with large? large = KB/MB/GB/TB ? Normally there is a task running which checks those log files and if they reach a certain size they get renamed and the task zips them with gzip.

---

### Post by jacktar on 2009-06-20
Well, not that large, about 2Mb, but the system has only been loaded 4 days. If the system prevents them getting too large then no problem. Thanks.

---

### Post by Soul-Sing on 2009-06-20
Remember logfiles are an great instrument or tool to analyze your system, its behaviour, and can be used for troubleshooting.

---

