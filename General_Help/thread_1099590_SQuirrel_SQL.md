---
title: "SQuirrel SQL"
date: 2009-03-18
forum: General Help
---

### Post by mistypotato on 2009-03-18
Anyone use Squirrel SQL and know how to do a backup of a database ?

thx

---

### Post by charly4711 on 2009-03-18
SQuirrel SQL is typically not the best option to do DB backups. The databases themselves typically offer better tools. That being said, SQuirrelSQL has the ability to create SQL scripts from existing DBs. So you could select all the tables you want in the tree browser and then find the scripts section and smth. like "Generate Data Script". That gives you an SQL script you can run on an empty DB to recreate you current one.

Be warned! Depending on your DB, the script generation can take a LONG time and eat A LOT of memory.

---

### Post by mistypotato on 2009-03-18
thx for the reply :D

Would you have a suggestion for backing up a remote database other than SQuirrel?

Cheers

---

