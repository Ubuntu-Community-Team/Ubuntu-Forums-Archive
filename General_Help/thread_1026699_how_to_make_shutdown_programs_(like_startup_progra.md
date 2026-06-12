---
title: "how to make shutdown programs (like startup programs)"
date: 2008-12-31
forum: General Help
---

### Post by change.chases.me on 2008-12-31
We always have option for putting a program in startup list, so that on system startup they are automatically invoked. But what if we want that program to run automatically before shutdown ?
Is there a way ??

---

### Post by dcstar on 2008-12-31
> **change.chases.me said:**
> We always have option for putting a program in startup list, so that on system startup they are automatically invoked. But what if we want that program to run automatically before shutdown ?
Is there a way ??

All shutdown scripts are in /etc/rc0.d, have a look in there.

---

