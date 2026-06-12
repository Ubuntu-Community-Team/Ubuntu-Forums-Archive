---
title: "PostgreSQL"
date: 2006-01-20
forum: Desktop Environments
---

### Post by jaywatkins on 2006-01-20
Hi,

Does anyone knowwhere Ubuntu hides the createdb command after one would install postgresql?

Thanks

---

### Post by browneyedgirl65 on 2006-02-02
After installation on mine, it appears to be /usr/bin/createdb (use the locate command).

ps -elf | grep postmaster should also tell you where it put the database.

(This is assuming installation via synaptic: I don't know what manual installations wind up doing; the documentation over at [http://www.postgresql.org/docs/8.0/interactive/installation.html](http://www.postgresql.org/docs/8.0/interactive/installation.html) makes different assumptions...)

---

### Post by jaywatkins on 2006-02-13
Thanks man!!!

---

