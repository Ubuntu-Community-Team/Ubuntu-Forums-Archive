---
title: "Problems with backport sever"
date: 2005-08-16
forum: Desktop Environments
---

### Post by pixelnate on 2005-08-16
I am having a problem with the mirrormax.net backport server. I keep getting 404 errors when I apt-get update. Has something happened to that server or is there a better server to find backports? Thx.

---

### Post by jasmuz on 2005-08-16
Exchange your mirrormax.net backport servers for these:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

---

### Post by pixelnate on 2005-08-16
Thank you very much.

---

