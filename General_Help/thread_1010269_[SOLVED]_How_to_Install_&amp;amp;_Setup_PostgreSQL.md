---
title: "[SOLVED] How to Install &amp;amp; Setup PostgreSQL for Intrepid"
date: 2008-12-13
forum: General Help
---

### Post by rich1939 on 2008-12-13
I've read the documentation for using Apt to get postgresql-8.3 for Hardy, but I'm using Intrepid (8.1) and I'd like to get the latest version of PostgreSQL as well. Also, the current Ubuntu documentation seems only to have Server setup for Dapper, Gutsy/Hardy.

Can I use these same commands to install and setup PostgreSQL 8.3 for Intrepid (i.e., sudo apt-get install postgresql-8.3)?

And, also, what are the commands for setup, creating a password, etc., for Intrepid?

---

### Post by nielz on 2008-12-13
sudo apt-get install postgresql will do the trick, since 8.3 is the default version now.

If you tell me what you'd like to setup I can help you iwth the commands.

---

### Post by rich1939 on 2008-12-13
> **nielz said:**
> sudo apt-get install postgresql will do the trick, since 8.3 is the default version now.

If you tell me what you'd like to setup I can help you iwth the commands.

Great! Thanks a bunch. I guess I just need to setup a password and then setup a database. After that, I hope to be able to access, add and modify entries using C and GTK+, but I wanted to setup the database first...and then find out about the C/GTK+ interfaces to the product.

---

### Post by nielz on 2008-12-13
All right! Postgres is a great choice for a database. I have no experience with interfacing with postgres using C or GTK+ but you will have to setup a user first.

You can connect to postgres using a tcp socket or a unix domain (local) socket. If you use the local socket you won't need to enter a password because postgres will check if your (linux) username is the same as your postgres username. 

To setup your first user you'll need to create a database (super)user account for yourself, you can do this using (be sure to replace yourlinuxusername with your actual username, it's important it matches your linux username):

```

sudo su -c "createuser yourlinuxusername --superuser" -- postgres

```

You can now create a test database for yourself. Running createdb without a name will create a database with the same name as your user, but you can also supply another name:

```

createdb

```

If you start the psql postgres client it'll automagically log in to the the database you just created because it has the same name as you user. If you named your database different you can use that name as an argument.

```

psql
Welcome to psql 8.3.5, the PostgreSQL interactive terminal.

Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit

yourlinuxusername=# 

```

And that's the basic setup. You may now type sql :)

---

### Post by rich1939 on 2008-12-13
[QUOTE=nielz;6362758]All right! Postgres is a great choice for a database. I have no experience with interfacing with postgres using C or GTK+ but you will have to setup a user first.

```

sudo su -c "createuser yourlinuxusername --superuser" -- postgres

```

Thanks...but I think I screwed up. My linux prompt is "richard@satin", but when I typed the above command, I only typed "richard" for my linuxusername. I also wasn't sure whether the "-- postgres" part of the command was meant to have a space between the dashes and the postgres, but I left it there when I typed the command. The result was an immediate ">" prompt.

I then typed the following, all with no response from the system, except the prompt:

```

> createdb
> psql
> exit
>
```

And then, when nothing happened, I did a Ctrl-C abort. Then I typed:

```

**richard@satin:~$**createdb

```

But this resulted in an error message, as follows:
"createdb: could not connect to database postgres: FATAL Ident authentication failed for user "richard""

I then tried again to type the following command:

```

sudo su -c "createuser richard@satin --superuser -- postgres

```

But it responded with the following:

```

su: unrecognized option '--superuser'

```

I'm afraid that I've screwed the pooch and want to know how to recover and enter the proper commands to setup my user name and create the initial database.

I sure appreciate your help.

-richard-

---

### Post by nielz on 2008-12-13
The part after the @ is your hostname and you forgot a double quote ("). Try this:

```

sudo su -c "createuser richard --superuser" -- postgres

```

edit: after doing this you should be able to run the other commands normally

---

### Post by rich1939 on 2008-12-13
> **nielz said:**
> The part after the @ is your hostname and you forgot a double quote ("). Try this:

```

sudo su -c "createuser richard --superuser" -- postgres

```

edit: after doing this you should be able to run the other commands normally

Ahhhhh! You're right! Thanks very much. Now I'll have to read the PostgreSQL docs to see how to add tables to the database, etc.

I also saw some mention of a graphic administration tool. Is that something that I should also install?

Thanks again for the rescue. These forums are really the best in the world...and you're a great help.

---

### Post by nielz on 2008-12-13
Thats quite allright I'm happy to help! (And thank you for all those thanks)

There's a graphical client called pgadmin3, it's in the repositories. 

If you're going to connect to your local database, you'll need to leave the "Host" field blank. If you don't it'll try to connect over tcp/ip which requires a password which you have not yet set.

Good luck!

---

### Post by Pravin16 on 2010-01-20
i succesfully installed postges from dvd. but ruuning on comand line 
it gives error like bash coomand not found.
posgres

---

