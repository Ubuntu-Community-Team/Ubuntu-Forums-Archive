---
title: "Evolution, Apport-gtk, Sqlite3 problem."
date: 2009-04-20
forum: General Help
---

### Post by inunu on 2009-04-20
If anyone can help me with some info on the following errors I'd really appreciate it. My thinking is that its a problem with sqlite I've tried re-installing Evolution, Apport and Sqlite

$ evolution
** (evolution:10635): DEBUG: mailto URL command: evolution %s
** (evolution:10635): DEBUG: mailto URL program: evolution
evolution: symbol lookup error: /usr/local/lib/libsqlite3.so.0: undefined symbol: sqlite3BackupRestart

$ /usr/share/apport/apport-gtk -c %f
Could not import module, is a package upgrade in progress? Error: no module named sqlite3 or pysqlite2.dbapi2

---

