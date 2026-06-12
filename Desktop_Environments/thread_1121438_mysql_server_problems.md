---
title: "mysql server problems"
date: 2009-04-10
forum: Desktop Environments
---

### Post by cybernet on 2009-04-10
i installed mysql server 5 on mysq ubuntu 8.04, it worked

i replaced mysql database with an old mysql database from a previous install ( because i have my users and passwords there )

but i forgot to create a backup of new mysql database

then mysql won't start because debian-sys-maint user doesn't know the password , and i can't change it because ./mysql/user.frm is readonly ( i guess it's a security measure from mysql server )

i thought if i will delete /etc/mysql/* & /etc/init.d/mysql* it will reinstall mysql like it was never installed , but no it didn't happened 


now i'm asking you guys if can give me those files in an archive
( i don't try to hack your server :lolflag: )
please help :D

thank you,
cybernet

---

### Post by ahbart on 2009-04-10
You could try to remove mysql stuff in synaptic with the 'remove all' including config files. And then install it again. This might work.

---

