---
title: "Unity search not working after  zeitgeist issue"
date: 2011-11-01
forum: Desktop Environments
---

### Post by Jasper91 on 2011-11-01
Hi everyone,

A few moments ago my zeitgeist-daemon was running at 100% CPU for quite a while. Attempts to restart the daemon failed with the message:
```
[INFO - zeitgeist.sql] Using database: /home/jasper/.local/share/zeitgeist/activity.sqlite
Traceback (most recent call last):
  File "/usr/bin/zeitgeist-daemon", line 198, in <module>
    main()
  File "/usr/bin/zeitgeist-daemon", line 176, in main
    mainloop, interface = setup_interface()
  File "/usr/bin/zeitgeist-daemon", line 103, in setup_interface
    return mainloop, RemoteInterface(mainloop = mainloop)
  File "/usr/share/zeitgeist/_zeitgeist/engine/remote.py", line 71, in __init__
    self._engine = get_engine()
  File "/usr/share/zeitgeist/_zeitgeist/engine/__init__.py", line 42, in get_engine
    _engine = main.ZeitgeistEngine()
  File "/usr/share/zeitgeist/_zeitgeist/engine/main.py", line 99, in __init__
    self._cursor = cursor = get_default_cursor()
  File "/usr/share/zeitgeist/_zeitgeist/engine/sql.py", line 494, in get_default_cursor
    _cursor = create_db(dbfile)
  File "/usr/share/zeitgeist/_zeitgeist/engine/sql.py", line 212, in create_db
    cursor.execute("PRAGMA journal_mode = DELETE")
  File "/usr/share/zeitgeist/_zeitgeist/engine/sql.py", line 76, in execute
    return super(UnicodeCursor, self).execute(statement, parameters)
sqlite3.OperationalError: database is locked
```

I removed zeitgeist-extension-fts and tried to restart my computer, but Ubuntu froze during shutdown.

After I logged in again, my Unity search was broken. I cannot search for applications, when I for instance click the Media Apps-button, Unity crashes!

I tried reïnstalling the zeitgeist extension, rebooting (again freeze during shutdown) and restarting zeitgeist.. but without result!

Help would be highly appreciated!

---

### Post by Jasper91 on 2011-11-01
Problem was solved by:

 - Removing and reinstalling zeitgeist, zeitgeist-extension-fts
 - Removing, reinstalling and restarting Unity
 - Using Ubuntu Software Center to reindex the installed applications

EDIT: Zeitgeist back @ 100% CPU usage......

---

### Post by David006 on 2011-11-13
try clearing all indices (vern. 'indexes') and history:

clear history:
```
  zeitgeist-daemon --quit

  ls -l ~/.local/share/zeitgeist/

  sudo rm ~/.local/share/zeitgeist/activity.sqlite.bck  (if present)
  sudo rm ~/.local/share/zeitgeist/activity.sqlite-journal  (if present)
  sudo rm ~/.local/share/zeitgeist/activity.sqlite
```

restart:
```
  zeitgeist-daemon &
```

---

