---
title: "Need help with configuring dpkg for update."
date: 2009-04-15
forum: General Help
---

### Post by wolfman1221 on 2009-04-15
I was trying to update my system and I received this message. 


"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
"


I am new, so if anyone could help me figure this out, I would be very grateful.

---

### Post by Sealbhach on 2009-04-15
This happens quite often. The error message actually gives you the solution. Open a terminal and copy and paste this into it:

```
sudo dpkg --configure -a
```

Enter your password when asked.

That should fix it.


.

---

### Post by wolfman1221 on 2009-04-15
This is what came up after I put in my password.


"dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory"

---

### Post by Sealbhach on 2009-04-15
Hi, try this:
```

sudo dpkg-reconfigure -phigh apt
```

.

---

### Post by wolfman1221 on 2009-04-15
This is what came back.



"dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt is not installed"

---

### Post by Sealbhach on 2009-04-15
I don't know anything else you could try. I would suggest you start a new thread with this in the title:

/usr/sbin/dpkg-reconfigure: apt is not installed


.

---

