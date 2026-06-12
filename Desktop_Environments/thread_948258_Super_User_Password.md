---
title: "Super User Password"
date: 2008-10-15
forum: Desktop Environments
---

### Post by abdulazizttk on 2008-10-15
:mad:
I forgot my SU password.. How to retrieve my SUPER USER PASSWORD ??
Please Help me...........
:(

---

### Post by kerry_s on 2008-10-15
if you still have sudo privileges just set a new one.

```
sudo passwd root
```

just a reminder you do not need a root password, everything can be done with sudo/gksudo you should just lock root back up.

```
sudo passwd -l root
```

---

