---
title: "MySQL 1018 ERROR 1018 (HY000): Can't read dir of './fdwp2/' (errno: 13)"
date: 2008-12-03
forum: General Help
---

### Post by wiseland on 2008-12-03
I have a db named fdwp2.
Then I use symb link ~fdwp2 to fdwp2 (it's locate in another disk) I get such error ERROR 1018 (HY000): Can't read dir of './fdwp2/' (errno: 13)
Then I replace my db to /var/lib/mysql it works wonderfully.

I set all rights to fdwp2 and to all files inside this dir.
drwxrwxrwx 2 mysql mysql        4096 2008-12-03 19:24 fdwp2

I can't have fdwp2 in /var/lib/mysql, because I haven't such enough place.
Why if I use symb link ~fdwp2 MySQL can't allow access to db.

Please help me!

P.S. This error appeared after I did full update of my Ubuntu system.
Early it works using symb link :(

---

### Post by wiseland on 2008-12-04
I've solved this problem.
The problem was in /etc/apparmor.d/usr.sbin.mysql file
It was need to add path to my db in this file :)

---

