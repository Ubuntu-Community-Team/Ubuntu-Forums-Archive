---
title: "Postgresql FATAL:  user &quot;root&quot; does not exist&quot;"
date: 2005-06-21
forum: Desktop Environments
---

### Post by cgetty on 2005-06-21
Hi
I'm using kUbuntu.
using the package manager I installed Postgresql.

When my PC boots up I see it (Postgresql) loadup.

When I try to add a user of create a database I get an error.

For example when I try to create a database:
cgetty@clark:~$ sudo -s -H
createdb mydb

I get this
"createdb: could not connect to database template1: FATAL:  user "root" does not exist"

Any one have any ideas ?

Thanks
Clark

---

### Post by geearf on 2005-06-21
Maybe you need to create a root user, as you don't really have one as default.

---

### Post by Firetech on 2005-06-21
[QUOTE=geearf]Maybe you need to create a root user, as you don't really have one as default.[/QUOTE]
 That's not entirely true. The root user of the system exists (it has to), it is just locked, so you cant log in using the username "root".

I guess that Postgresql is missing the user "root" itself (I've never tried Postgresql, I'm satisfied with MySQL). Try running the createdb command as yourself, I don't really know how the Postgresql installation works.

---

### Post by Juergen on 2005-06-21
The only database-user after install is 'postgres' i.e. the owner of the database-process.

You should start with 'su - postgres' and add an user with your normal username (and give rights to create databases/users to yourself).

After that you should be able to do db-administration with your normal account.

---

### Post by cgetty on 2005-06-21
Thanks all for your help.

Juergen, your solution worked.

now I'm off & running

Clark

---

