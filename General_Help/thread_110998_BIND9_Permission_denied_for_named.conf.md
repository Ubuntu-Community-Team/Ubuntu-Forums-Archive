---
title: "BIND9 Permission denied for named.conf"
date: 2006-01-01
forum: General Help
---

### Post by rensu on 2006-01-01
loading configuration from '/etc/bind/named.conf'
none:0: open: /etc/bind/named.conf: permission denied
loading configuration: permission denied
exiting (due to fatal error)

Can anyone help me? What's going on:((

---

### Post by schilcha on 2006-01-01
Did you run bind as (sudo) root? 

Did you check on the file-access permissions of the file (readable for the UID executing bind) and the containing directory (also needs execute-permission).

I once set up bind9 on suse. There, a tool "named-checkconf" existed, which reported configuration errors -- if you have it, try it.

Good Luck!

---

### Post by yonkman on 2008-05-29
found fix here

[http://www.howtoforge.org/forums/showthread.php?p=116893](http://www.howtoforge.org/forums/showthread.php?p=116893)

---

### Post by Joeb454 on 2008-05-29
No offence, but I'd imagine that the fix isn't needed anymore, as the last post in this thread was January 1st 2006 ;)

---

### Post by Perfect Storm on 2008-05-29
Closed due to necromancing.

---

