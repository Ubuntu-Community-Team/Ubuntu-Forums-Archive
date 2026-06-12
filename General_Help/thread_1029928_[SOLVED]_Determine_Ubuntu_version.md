---
title: "[SOLVED] Determine Ubuntu version ?"
date: 2009-01-03
forum: General Help
---

### Post by zami on 2009-01-03
What Ubuntu am I using?

System > About Ubuntu 
says to me
> Thank you for your interest in Ubuntu - the - released in ."

Is there a command line I can query my machine with for this info?

Thanks!

-zami

---

### Post by adult swim on 2009-01-03
a couple are ```
lsb_release -a

cat /etc/issue
```

---

### Post by zami on 2009-01-03
lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid


Perfect, thank you!

-zami

---

