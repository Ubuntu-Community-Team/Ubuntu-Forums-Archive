---
title: "mysql problem with new accounts"
date: 2009-03-08
forum: General Help
---

### Post by Milambar on 2009-03-08
My MySQL install seems to be borked.

Basically, for example, if I create a database called: thedb with
create database thedb;

Then run: 
grant all privileges on thedb.* to user identified by 'password';

The db and the user is formed properly. the show grants for user shows they have all privileges on that db, but when I try and log in as that user with

mysql -u user -p

and give my password, and no, Im not mistyping it, Ive checked that, it still refuses access to the db. 
```

ERROR 1045 (28000): Access denied for user 'user'@'localhost' (using password: YES)

```

The db works perfectly if I log in as root. (mysql -u root -p). All I can think of is that MySQL is not crypting the password correctly.

Can anyone offer any suggestions?

---

### Post by hyper_ch on 2009-03-08
you need to reload the user privileges by flushing mysql.

---

### Post by warp99 on 2009-03-08
I have the same problem, but if I use this syntax:

```
mysql -u $USER --password=$PASSWORD
```

I can login just fine.

---

