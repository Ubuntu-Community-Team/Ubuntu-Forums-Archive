---
title: "Update 7/13/2006: Samba package broken"
date: 2006-07-13
forum: Desktop Environments
---

### Post by th3gh05t on 2006-07-13
Hi, 

With the latest update to the "Samba" package, I am receiving this error:

```
E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb: subprocess new pre-removal script returned error exit status 102
```

Is anyone else receiving this error? Is it known that this is an issue?

Regards,
th3gh05t

---

### Post by OldTimeTech on 2006-07-13
Check this link out, might help you take care of the problem.

[http://www.ubuntuforums.org/showthread.php?t=214444](http://www.ubuntuforums.org/showthread.php?t=214444)

---

### Post by th3gh05t on 2006-07-13
Thanks!

These commands worked perfecty:

first delete files:

sudo rm /etc/rc3.d/K09samba

sudo rm /etc/rc2.d/K09samba

and than:

sudo apt-get remove samba

and new installation:

sudo apt-get install samba

---

