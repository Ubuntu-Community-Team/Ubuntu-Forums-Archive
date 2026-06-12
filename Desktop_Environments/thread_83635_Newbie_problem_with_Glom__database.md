---
title: "Newbie problem with Glom / database"
date: 2005-10-29
forum: Desktop Environments
---

### Post by ad noiseam on 2005-10-29
Hello,

New to Linux, I am trying to use Glom ([www.glom.org](www.glom.org)) to work (and learn) on a small database created with FileMaker on Windows.

I have installed Glom, but, when I try to run it, it asks for the connection details to my database server. By default, the host is "localhost" and the user is my Ubuntu username. However, my Ubuntu password doesn't work, and I get this error message:

> 
Connection Failed

Glom could not connect to the database server. Maybe you entered an incorrect user name or password, or maybe the postgres database server is not running.


I have not installed any database server, or anything of the kind. Does anybody know what I should do to get Glom working?

Thank you,

Nicolas

---

### Post by ad noiseam on 2005-10-29
if it helps, here is the output of Glom at startup ("nicolas" being my Ubuntu username, and I am leaving the password blank (same result if I use the Ubuntu password).

```

nicolas@ubuntu:~$ glom
connecting: cnc string: HOST=localhost;USER=nicolas;PASSWORD=;DATABASE=glom_exam ple_smallbusiness_v10
ConnectionPool::connect() Attempt to connect to database failed: glom_example_sm allbusiness_v10
  ConnectionPool::connect() Attempting to connect without specifying the databas e.
connecting: cnc string: HOST=localhost;USER=nicolas;PASSWORD=;DATABASE=template1
    ConnectionPool::connect() connection also failed when not specifying databas e.

** (glom:9523): WARNING **: ConnectionPool::connect() throwing exception.

** (glom:9523): WARNING **:   (Could not connect even to the default database.)

** (glom:9523): WARNING **: Frame_Glom::connection_request_password_and_attempt( ): caught exception.
connecting: cnc string: HOST=localhost;USER=nicolas;PASSWORD=;DATABASE=glom_example_smallbusiness_v10
ConnectionPool::connect() Attempt to connect to database failed: glom_example_smallbusiness_v10
  ConnectionPool::connect() Attempting to connect without specifying the database.
connecting: cnc string: HOST=localhost;USER=nicolas;PASSWORD=;DATABASE=template1
    ConnectionPool::connect() connection also failed when not specifying database.

** (glom:9523): WARNING **: ConnectionPool::connect() throwing exception.

** (glom:9523): WARNING **:   (Could not connect even to the default database.)
Glom: exception:

```

And this is after having done what's written at [http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration](http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration)
:(

Nicolas

---

### Post by Neeko on 2005-10-29
Well, I dont use Glom, but I thought it only worked with postgresql tables it created, ie it wont work natively with Filemaker?

---

### Post by ad noiseam on 2005-10-30
I guess there is a way to import databases from FileMaker to Postgres or Glom, and therefore work with Glom on a database which I first developped in XP. Anyway, what I have here is very simple.

Still, has *anybody* been able to use Glom on Breezy?

---

### Post by jon_gunnar on 2005-10-30
[QUOTE=ad noiseam]Hello,

I have not installed any database server, or anything of the kind. Does anybody know what I should do to get Glom working?

Nicolas[/QUOTE]

You states that you don't have installed any kind of databse server, but the Glom Initial Configuration says that it needs a postgres server.
[http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration](http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration)

---

### Post by ad noiseam on 2005-10-30
[QUOTE=jon_gunnar]but the Glom Initial Configuration says that it needs a postgres server.[/QUOTE]

I did create the database as indicated on this page, but I have no idea whether I have a Postgres server, how to check if I do, and how to set one up if I don't. :-/

---

### Post by eewald on 2006-05-28
[QUOTE=ad noiseam]I guess there is a way to import databases from FileMaker to Postgres or Glom, and therefore work with Glom on a database which I first developped in XP. Anyway, what I have here is very simple.

Still, has *anybody* been able to use Glom on Breezy?[/QUOTE]
i followed the exact same instructions, but no luck...

---

### Post by p0pnfresh on 2006-08-28
I'm also trying to work with Glom. 

You should start by running Synaptic and installing postgresql-8.1. This will install both the server and client. 

Install.

You have to create a new ubuntu user named "postgres". 

Login as postgres and type $createdb glom_mydatabase. Glom uses the suffix glom_. 

Iv'e done this so far but still Glom doesn't connect to my postgres, which is set at localhost.

It would be useful to know how to start and stop the postgres server.

Has anyboby been successfull using Glom?

](*,)

---

### Post by murrayc on 2006-09-25
> **p0pnfresh said:**
> I'm also trying to work with Glom. 

You should start by running Synaptic and installing postgresql-8.1. This will install both the server and client.


On Breezy, Postgres 7.4 is the default. That's why the Glom instructions mention changing the 7.4 configuration files on Breezy. The Dapper instructions might work if you install 8.1 on Breezy, but something else might be different.

> **p0pnfresh said:**
> I'm also trying to work with Glom. 
You have to create a new ubuntu user named "postgres". 


No, this user will exist already. I think it's created by the postgres installation.

> **p0pnfresh said:**
> 
I'm also trying to work with Glom. 
Login as postgres and type $createdb glom_mydatabase. Glom uses the suffix glom_. 


No, you never need to create a database manually. Glom does this for you. In fact, Glom offers no (easy) way to use an existing posgres database.

> **p0pnfresh said:**
> 
Iv'e done this so far but still Glom doesn't connect to my postgres, which is set at localhost.


Mayeb you need to double-check that you have specified that postgres should accept TCP connections and that it listens on all IP addresses, as mentioned in the instructions.

You might also try pgadmin3 to try to make a connection to the postgres server, to check that it's basically working.

> **p0pnfresh said:**
> 
It would be useful to know how to start and stop the postgres server.


This should be possible via the Services control panel.

If you need more help, email the Glom mailing list. I won't check this site very often.

---

### Post by pismo on 2006-11-11
After much ](*,)  i got Glom up and running by using this howto I started with the config files first and then the adding user last hope it help :p 

[http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration](http://www.glom.org/wiki/index.php?title=Initial_Postgres_Configuration)

---

### Post by mynona on 2006-11-25
> **p0pnfresh said:**
> I'm also trying to work with Glom. 

Has anyboby been successfull using Glom?

](*,)

Today I've installed Glom 1.03 and Postgresql 8.1 (Dapper) with some minor problems. Now all is running, but I think Glom is not useable, it's always crashing...
So I want to ask the same:

Is anybody working sucessfully with a Glom database? Maybe with a newer version in Edgy?

---

### Post by murrayc on 2006-12-11
Yes, it would be really nice if Ubuntu would update its Glom version without forcing you to update your entire distro. So many bugs (including many crashes) have been fixed.

---

### Post by teeleef on 2007-02-03
Guys,  I managed it by when creating a database I used the glom extension eg. glom_exampledatabase.glom

It worked!!!


Teeleef

---

