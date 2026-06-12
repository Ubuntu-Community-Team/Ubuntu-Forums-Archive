---
title: "[SOLVED] Root password in gnome ?"
date: 2008-11-23
forum: Desktop Environments
---

### Post by D4mn on 2008-11-23
Hi all.

I changed the root password and /etc/sudoers on my system for normal root access. Now when gnome asks me for an admin password, my normal user password is needed :confused:. I have no idea where to start looking (google did not help here either).

Thanks in advance!
Danny

---

### Post by sisco311 on 2008-11-23
type:
```
gksu-properties
```in a terminal and set the authentication mode to su.

---

### Post by D4mn on 2008-12-03
Works, thanks.

---

