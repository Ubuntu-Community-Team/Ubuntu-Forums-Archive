---
title: "Check disk at startup problem"
date: 2009-06-09
forum: General Help
---

### Post by kounabi on 2009-06-09
Hey!!

I m new to this forum although i m not new to linux. The problem is this:
I recently upgraded to 9.04.Since then when i get a check disk at boot it suddenly stops checking and does nothing.........for any further information  please post....

Thanks!!!

---

### Post by MimziM on 2009-06-09
try booting from a live cd
when you have a desktop
open a terminal and run
```
user@home:~$ fsck 
```

---

### Post by kounabi on 2009-06-09
thnx for the reply!!

the result of fsck through live cd is:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 271797/5136384 files, 3922731/20523029 blocks
```Actually some times its the check which stops and sometimes the screen just doesn' t show the progress...its not the second which concerns me but the first....

I m not sure if it ran properly cause it just took about a second to finish but it seems that the disk is ok (it should be cause its almost new).
So what could be wrong....???

---

### Post by kounabi on 2009-06-12
anybody plz.....

plzzzzzzzzzzzzzzzzzzzzzzzzz!!!

---

