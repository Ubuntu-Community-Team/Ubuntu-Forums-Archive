---
title: "Gimp dies on File-&gt;Open"
date: 2005-06-09
forum: Desktop Environments
---

### Post by mossholderm on 2005-06-09
Andy ideas what would cause this? It occurs each time I try to get to the File->Open dialog in Gimp-2.2. Feeding in filenames on the command-line works properly. I'm running 2.2.6-1~5.04ubp1, but the same thing happens if I force the version to the standard Ubuntu version.

     --Matt

```
mattcm@mourneblade:~$ gimp-2.2
gimp-2.2: pthread_mutex_lock.c:78: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.
gimp-2.2: terminated: Aborted
mattcm@mourneblade:~$
(script-fu:6517): LibGimpBase-WARNING **: script-fu: wire_read(): error
```

---

### Post by Burgundavia on 2005-06-09
File a bug about it:

bugzilla.ubuntu.com

Corey

---

