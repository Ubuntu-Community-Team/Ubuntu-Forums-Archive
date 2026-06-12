---
title: "[SOLVED] MySql - not able to connect db as new-user"
date: 2008-12-15
forum: Desktop Environments
---

### Post by andrea_wwubuforum on 2008-12-15
Hi all,
i've just installed UBUNTU 8.10 (first I was a 7.10 user) and MySQL 5.0.67-0ubuntu6

My problem with MySql is that I'm not able to connect the database server as user different from the root.

As root I've no problem, I can connect an query the database.

I've created a new user "test", using MySql Administrator tool as root.

When I try to connect the database as "test" the following error is thrown by mysql:

Could not connect to host 'localhost'.
MySQL Error Nr. 1045
Access denied for user 'test'@'localhost' (using password: YES)

Click the 'Ping' button to see if there is a networking problem.

If I try the Ping the server will correct respond

I think that is a permission problem but I try in any way without results..

Can anyone help me?

Thanks in advance...
Andrea.

---

### Post by trentscott4 on 2008-12-15
You need to set the host permissions for that user as 'localhost' from MySQL administrator.  Otherwise, it will deny the connection.

---

### Post by andrea_wwubuforum on 2008-12-15
thanks trentscott4,
once set the localhost permissions the connection is established.:p

problem solved!

Just for other users...
setting the permissions for @ % seems be not enough...

best regards!

Andrea.

---

