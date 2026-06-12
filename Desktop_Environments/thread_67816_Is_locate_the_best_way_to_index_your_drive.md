---
title: "Is locate the best way to index your drive?"
date: 2005-09-21
forum: Desktop Environments
---

### Post by Deekin on 2005-09-21
Hi all:

I remember locate -u and locate form my earlier UNIX days. Is there something better now to do a search on your drive?

---

### Post by Xiata on 2005-09-21
[QUOTE=Deekin]Hi all:

I remember locate -u and locate form my earlier UNIX days. Is there something better now to do a search on your drive?[/QUOTE]
 ew... you don't use find / -name ?

you dont need to -u, ubuntu cronjobs updatedb daily.

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=Deekin]Hi all:

I remember locate -u and locate form my earlier UNIX days. Is there something better now to do a search on your drive?[/QUOTE]
You can use slocate-- it won't show files you don't have access to.

---

### Post by bsussman on 2005-09-21
[QUOTE=cwaldbieser]You can use slocate-- it won't show files you don't have access to.[/QUOTE]

On a default ubuntu system locate **IS** slocate:

 ```
root@Dillon:~ # type slocate
slocate is /usr/bin/slocate
root@Dillon:~ # ls -l /usr/bin/locate
lrwxrwxrwx  1 root root 7 Aug 29 20:35 /usr/bin/locate -> slocate
```

---

