---
title: "PenguinTV troubles"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Bo Rosén on 2006-08-20
I Installed PenguinTV from the repos yesterday to try, and liked what I saw. But the version in the repos is old so I went and got the 2.0.1 version and had no problems installing and playing with that. But now it won't start. Any suggestions?


```
brosen@Delirium:PenguinTV 
Traceback (most recent call last):
  File "/usr/bin/PenguinTV", line 41, in ?
    penguintv.main()
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 1282, in main
    app = PenguinTVApp()    # Instancing of the GUI
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 92, in __init__
    self.firstrun = self.db.maybe_initialize_db()
  File "/usr/lib/python2.4/site-packages/penguintv/ptvDB.py", line 133, in maybe_initialize_db
    self.migrate_database_one_two()
  File "/usr/lib/python2.4/site-packages/penguintv/ptvDB.py", line 150, in migrate_database_one_two
    self.c.execute(u"""CREATE TABLE tags
pysqlite2.dbapi2.OperationalError: table tags already exists
```

EDIT: renaming the ~/.penguintv folder solved this, but having to reenter all my feeds and downloading everything again will take a while.

---

