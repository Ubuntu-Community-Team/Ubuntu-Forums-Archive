---
title: "iODBC"
date: 2009-02-20
forum: General Help
---

### Post by Chris5699 on 2009-02-20
As a noob, I posted in the wrong section :)

Hello all,

I am a linux noob to a vast extent. I am currently trying to connect to a Intersystems Cache database (on another server) utilizing PHP (running on Apache). I believe that I need to install iODBC for this to happen (just like I needed to install freeTDS to connect to MSSQL). Could someone supply some detailed step by step instructions on this install process? I've installed iodbc, libiodbc2 and libiodbc2-dev via the apt-get install process, but there are other considerations. I set a set environmental variables piece, but can't find anything on this process (as an example). Any help would be greatly appreciated.

Reply:
Ah, this one might be a bit more useful, I guess: [http://www.iodbc.org/index.php?page=.../odbc-phpHOWTO](http://www.iodbc.org/index.php?page=.../odbc-phpHOWTO)

Reply:
Yes, I have used those pages to get me this "far". But there are items in there (like set env_variable) that I don't know how to do. What is the step by step process to set and env_variable?

I know my work isn't done because PHP doesn't recognize the odbc_connect function yet...

---

