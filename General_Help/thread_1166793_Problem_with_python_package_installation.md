---
title: "Problem with python package installation"
date: 2009-05-22
forum: General Help
---

### Post by colau on 2009-05-22
```

apt-get install python python-glade2 python-gnome2 python-sqlite3 python-gconf rsync 

```
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
python-glade2 is already the newest version.
python-gnome2 is already the newest version.
E: Couldn't find package python-sqlite3

```

---

### Post by severedspirit on 2009-05-22
There isn't a package for python-sqlite3 in the current ubuntu repository, use python-pysqlite2 instead

---

### Post by colau on 2009-05-22
> **severedspirit said:**
> There isn't a package for python-sqlite3 in the current ubuntu repository, use python-pysqlite2 instead
Ok,Thanks.

---

