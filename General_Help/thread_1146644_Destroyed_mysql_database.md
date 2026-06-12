---
title: "Destroyed mysql database"
date: 2009-05-02
forum: General Help
---

### Post by dboucher on 2009-05-02
Hi, I feel pretty retarded for having to admit I did this, but:

I was manipulating some databases in mysql though the lampp installation, and I typed in "drop database mysql" through command line. I now am getting an error that says:

Can't connect to local MySQL server through socket '/opt/lampp/var/mysql/mysql.sock' (2)

I'm fairly confident that this can be solved by restoring the database the I deleted, but I'm not sure what steps to take to undo the damage that I have done. Any help with this is appreciated.

---

### Post by Alterax on 2009-05-02
I'm not sure you really can.  Not easily.  First, get MySQL running again.
Move your backups somewhere safe then run
```
sudo apt-get purge mysql-server

```
That'll completely wipe the borked install.

Next reinstall with
```
sudo apt-get install mysql-server
```

Now check to see if you can connect.  If so, you should be able to restore your DB from your backups

---

