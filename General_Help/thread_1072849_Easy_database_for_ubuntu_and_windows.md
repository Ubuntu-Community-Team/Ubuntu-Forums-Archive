---
title: "Easy database for ubuntu and windows"
date: 2009-02-17
forum: General Help
---

### Post by Luxman on 2009-02-17
Hello everybody :)

I need to setup a database to mantain a list of people with data related to them: the main purpose would be to be able to filter this list easily according to some features and eventually to create some statistics. I have no experience at all with databases but I am not afraid to learn ;)
I would be very grateful if you could point me out a software that could fit my needs, possibly easy to use and also available for Windows. Best of all would be if I could manage the database through a web browser.

Thank you very much for your help!

---

### Post by octesian on 2009-02-17
MySQL is pretty easy to learn.  I've never had to install it on my own though.

---

### Post by oldos2er on 2009-02-17
Open Office.

---

### Post by jerrrys on 2009-02-17
[http://www.zotero.org/](http://www.zotero.org/)

---

### Post by DGortze380 on 2009-02-17
> **oldos2er said:**
> Open Office.

x2

---

### Post by wirelessmonkey on 2009-02-18
sqlite?

---

### Post by jlokes on 2009-02-18
there is no built-in indexing mechanism support in linux ? 

It seems to be a very limited OS if you cant build a simple database without some third party vendor.

 That really sucks and makes me wonder if changing from windblows to linux is worth it :(

---

### Post by AcidHawk on 2009-02-18
I would suggest that you look at LAMP for linux and WAMP for windows.  Both of these are a complete install of Apache, Mysql and PHP.  These are not recomended for production but for you to get started in learning how to create a database and build a web frontend these will definately take the pain out of the installation piece and you can then focus on you specific requirement.

Nice thing is, is that if you build you db and web pages in linux you can simply copy them to a similar installation on windows and it will just work, and vise versa.

---

### Post by Luxman on 2009-02-18
Thank you for all your suggestions. Originally I was looking for something that can be managed by a web browser because other people have to deal with it and most of them completely unaware of how to use a computer except for the web browser... Moreover I thought that something like MySQL, SQLlite or PostgreSQL could be more powerful. Anyway I will have a look also at the OpenOffice solution.
I guess that installing and mantaining a LAMP/WAMP server goes a little beyond my actual needs. What I am looking for is a free/open and easy to implement solution to setup a database so that I can empower the work of the medical institution I am working in ;)

---

### Post by AcidHawk on 2009-02-19
Jeesh... I couldn't think of an easier way to setup a web server already configured to connect to a database than the LAMP/WAMP solution.  Both are 1 executable, run it and you can connect to localhost:8080 and can already see a web frontend to configure the database.  All you have to do is build the db and you own CRUD frontend and you are away.  

Google WAMP I think you'll be pleasently supprised.

---

### Post by Luxman on 2009-02-25
> **AcidHawk said:**
> Jeesh... I couldn't think of an easier way to setup a web server already configured to connect to a database than the LAMP/WAMP solution.  Both are 1 executable, run it and you can connect to localhost:8080 and can already see a web frontend to configure the database.  All you have to do is build the db and you own CRUD frontend and you are away.  

Google WAMP I think you'll be pleasently supprised.

Ok, I'll give it a try! Thanks ;)

---

