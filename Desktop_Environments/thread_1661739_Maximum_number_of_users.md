---
title: "Maximum number of users"
date: 2011-01-07
forum: Desktop Environments
---

### Post by gfreccia on 2011-01-07
How many users is it possible to set on Ubuntu 10.10?
I have an Edubuntu LTSP system for a school (10 clients) and I wish to setup an user for each student/teacher (about 200).

Thank you!

Giacomo.

---

### Post by doperative on 2011-01-07
> **gfreccia said:**
> How many users is it possible to set on Ubuntu 10.10?

Users are identified by unique UIDs, a 16 bit number, or 2 ^ 16, making for 65535 users. Newer version of the kernel use 32 bit UIDs.

[HighUID]("http://www.mjmwired.net/kernel/Documentation/highuid.txt")

---

### Post by gfreccia on 2011-01-07
Thanks!

---

