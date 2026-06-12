---
title: "Where is PostgreSQL Data in Ubuntu?"
date: 2005-12-15
forum: General Help
---

### Post by kennethb on 2005-12-15
I can't seem to find the file of my database I created in PostgreSQL on my Ubuntu Breezy box. I installed PostgreSQL using synaptic package manager. THe PostgreSQL website's documenation pages say my databases should be in:

/usr/local/pgsql/data

but they are not in that directory on my Breezy box. Can anyone suggest where I should look?

---

### Post by endersshadow on 2005-12-15
Check /var/lib/pgsql

---

### Post by kennethb on 2005-12-16
I don't have a /var/lib/pgsql directory, but I do have a:

/var/lib/postgresql/7.4/main

directory. Is this it? I can't access the 'main' directory using 'sudo cd main' command.

Any thoughts?

---

### Post by kennethb on 2005-12-16
[QUOTE=kennethb]I don't have a /var/lib/pgsql directory, but I do have a:

/var/lib/postgresql/7.4/main

directory. Is this it? I can't access the 'main' directory using 'sudo cd main' command.

Any thoughts?[/QUOTE]

OK, I figured out how to access the 'main' directory. I had to switch to the 'postgres' user:

ken@ubuntu:/var/lib/postgresql/7.4$ su postgres
Password:
postgres@ubuntu:~/7.4$ ls
main

The 'main' directory contains:

postgres@ubuntu:~/7.4/main$ ls
base    pg_clog      pg_ident.conf  pg_xlog          postmaster.opts  root.crt
global  pg_hba.conf  PG_VERSION     postgresql.conf  postmaster.pid

In looking in the 'base' directory, I see:

postgres@ubuntu:~/7.4/main$ cd base
postgres@ubuntu:~/7.4/main/base$ ls
1  17141  17142  17143

Are these the database directories?

I was thinking the databases would be directories named as the database (e.g., 'testdb'). I have the O'Reilly "Practical PostgreSQL" book, but I can't seem to find any info on the directory structure the PostgreSQL uses. Any help is very much appreciated and/or any direction as to where I can find this info. Thanks!

---

