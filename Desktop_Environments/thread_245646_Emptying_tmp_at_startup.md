---
title: "Emptying /tmp at startup"
date: 2006-08-28
forum: Desktop Environments
---

### Post by mumper13 on 2006-08-28
Having worked with suse and others I feel the need to empty the /tmp directory and, particularly, as an adjunct to startup. I recall mention of such a method/facility once in a Suse forum. Is there such a thing in Ubuntu?:confused: 
With thanks, mumper13

---

### Post by mssever on 2006-08-29
I imagine you could insert something like the following into /etc/rc.local:
```
rm -rf /tmp/*
``` That might run late enough that current processes already have stuff in /tmp. In that case, you could create a script in /etc/init.d/ with the above code and an appropriate shebang line (#!/bin/bash), make it executable, and symlink it into /etc/rc[2-5].d/ with S12 prepended to the name.

---

### Post by mf14 on 2006-09-08
On my installation (6.06 LTS Desktop) there is a script /etc/init.d/bootclean.sh  which does the job quite nicely! It is automatically called during each system boot by  
/etc/rcS.d/S35mountall.sh
Especially have a look at  .clean  and  $TMPTIME  in  /etc/default/rcS

But it is a pitty that the script deletes all files without any notice to the users new to the system, and the function seems not to be documented.

---

### Post by ayoli on 2006-09-08
/tmp as it  named is a temporary dir, debian (and debian based) policy is to clean /tmp at boot. users should not store files in /tmp

---

### Post by mumper13 on 2006-09-17
Sorry for the delay, but many thanks for the clarification - of course, on looking I found /tmp *had* been cleaned out, as advised.:D

---

