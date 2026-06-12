---
title: "Database creation and management! How? With which program?"
date: 2009-06-22
forum: General Help
---

### Post by edemark on 2009-06-22
Hi Everyone!

I have to create a not too difficult neither complicated database. However I have no idea which program to use and consequently have even less ideas on how to use them so. For this reason i have thought to ask you guys who might have better knowledge on this topic.
So here are my expectations towards the program:
-straightforward database creation (cases will have 30-50 variables to trace like: size, color, shape etc.)
-easy case management (I mean that after creating the layout of the database actual data of the cases can be entered easily)
-accessible (other people has to be able to collaborate on filling, changing data of the different cases, preference is that the net inter as much as intra will be used)
-interoperability (as a consequence of the previous point is that the program is accessible as much from linux as from windows and mac)
-at least some mathematical capabilities or possibility that created database can be used by other statistical programs (ok for the moment this is the least important question but in the longer run this might became important)
-free (at least for the moment i can not afford paying for the program)

Anyway any help would be really appreciated ie if you know a good site that deals with similar issues, as i am really inexpert on this matter.

Thanks for your help

---

### Post by mcduck on 2009-06-22
For easy, you could go with OpenOffice Base.  It's pretty much simple as database intended to be used by normal office workers can be, and runs on all Linux/OSX/Windows. Although I'm not sure about it's capabilities for working over networks, but I bet there's a way to get that working.

Of course there's always MySQL, but I wouldn't really call that "easy" and you'd probably have to create some web-based user interface for the database to make it usable for normal people.

---

### Post by credobyte on 2009-06-22
MySQL with MySQL Administrator ( standalone user interface ) or phpMyAdmin ( web based user interface ). It's definitely not the easiest one, but, you can learn it very quickly ( there are only a few keywords you need to remember ).

---

### Post by t0p on 2009-06-22
There's sqlite, but I know nothing about it. 'Cept it's lite.

OO Base is a simple one to run.

Mysql isn't exactly *harrrd*... well, it doesn't have to be. Plus it's a *full-featured* database solution, so when you want to upgrade, you don't need to!

---

### Post by The Cog on 2009-06-22
OpenOffice Base and anything based on sqlite are single-file, single-user solutions. Such a solution will involve having your users pass around and track the latest version of the document.

For proper multi-user collaborative development, I guess MySQL (or maybe PostgreSQL) is the way to go. The easiest way in is to let users use a GUI program like the mysql-query-browser, or make up an OpenOffice Base file that links to the MySQL server and distribute that.

---

### Post by edemark on 2009-06-22
Hi everyone!

Thanks for the replies. So far I feel that i shall choose sql to manage these task and the database. So I will start learning it now. I mean it does not have to be a too fancy database but functional. 
Anyway if you know for any reason some good tutorial or how-to the get started with MySQL, than please do not hesitate to post it here as it will be more than welcommed. Also if you have any further ideas or would like call my attention to any other possible resolution to my question than please do let me know. 

Thanks again for these replies and thanks in advance for the forthcoming ones if any.

---

### Post by The Cog on 2009-06-23
If you're starting off with MySQL, then installing it on Ubuntu is particularly easy.
**sudo aptitude install mysql, mysql-admin, mysql-query-browser**
will install it and get it running, listening for connections. Then you are ready to launch mysql-query-browser and log in as root (MySQL's administrator account) and start creating databases and other MySQL users. 

There are plenty of tutorials to google for. But remember that installing on Ubuntu as described above automatically does a lot of the grind for you - creating the needed directories, initialising the files and starting the MySQL database server process.

And just in case you don't realise it, MySQL itself is just a database server that runs in the background. To talk to it you need a client program. Running the command **mysql** from the command prompt is the default client but mysql-admin and mysql-query-browser are rather more friendly GUI clients.

---

