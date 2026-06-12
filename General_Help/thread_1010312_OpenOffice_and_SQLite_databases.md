---
title: "OpenOffice and SQLite databases"
date: 2008-12-13
forum: General Help
---

### Post by Jim Danner on 2008-12-13
When you install OpenOffice.org Database (3.0) through Add/Remove Programs, there is a reassuring message in the description: it can handle SQLite files, if you install a few packages.

That sounds good. I installed libsqliteodbc; unixodbc and SQLite were already there. But it's not that easy. I can't figure out what to do next. No help form Help, and nothing very clear on the internet.

A logical thing to do is "connect to existing database", of the ODBC type (since that package was called libsqlite*odbc*). But that's where it ends. Another one of those things that will only work for advanced users.

Does anyone have some step-by-step instructions on opening an SQLite database with OpenOffice now that I have these packages installed?

---

### Post by felker2 on 2008-12-14
Can [http://documentation.openoffice.org/HOW_TO/data_source/SQLite.pdf](http://documentation.openoffice.org/HOW_TO/data_source/SQLite.pdf) help?

---

### Post by Jim Danner on 2008-12-21
Thanks for that.

Apparently the description in Add/Remove Applications forgot to mention that you also need *unixodbc.bin*. Moreover, a connection to a database must be configured separately in the ODBCConfig utility and in OpenOffice.

Unfortunately, the set-up in OpenOffice doesn't work anymore in the way described in that document. I'm giving up. I'll try again in a few years, to see whether OpenOffice has decided to dedicate some attention to this hole in its functionality.

---

