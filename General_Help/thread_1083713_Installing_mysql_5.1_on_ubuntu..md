---
title: "Installing mysql 5.1 on ubuntu."
date: 2009-03-01
forum: General Help
---

### Post by BramWillemsen on 2009-03-01
Hello everybody.

I purchased a laptop a few days ago and i installed ubuntu on it. As a windows user, the learning curve is quite steep. I'm trying to install mysql-5.1.31 from a source file. I downloaded "Compressed GNU TAR archive (tar.gz) of 29.4 MB" from the source downloads tab of the mysql website.

I'm also using this guide [http://dev.mysql.com/doc/refman/5.1/en/quick-install.html](http://dev.mysql.com/doc/refman/5.1/en/quick-install.html) . Everything goes smooth up till point "make". I get the message "*** no targets specified and no makefile found. Stop." There is a makefile.am and a makefile.in file in the folder though. I've been trying to get it to work today but im really lost since i cannot find binaries for 64 bit ubuntu either. Every bit of help would be greatly appreciated!

btw i removed mysql 5.0.6 first that was automatically installed with ubuntu 8.10

kind regards, Bram

It seems like ./configure does not create a makefile from makefile.in. There is no error message though when i use ./configure

---

### Post by BramWillemsen on 2009-03-01
I guess the problem comes down to how make works in ubuntu. Do i have to use automake or something when there is a makefile.in and a makefile.out? I did not want to try this without confirmation because the rest of the guide might not work for me anymore then?

---

### Post by BramWillemsen on 2009-03-01
bump

---

### Post by arepaking on 2009-03-01
Hello Bram,
I happen to install mysql two days ago.

I followed this instructions and it worked at the very first attempt: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Let me know how it goes.

Regards,
ArepaKing

---

### Post by BramWillemsen on 2009-03-01
Hi, thanks for the suggestion, but won't that reinstall mysql 5.0.6 instead of 5.1 ? I bought a book about mysql, and they gave a guide to install LAMP piece by piece. When compiling php, a link to the mysql_config is needed file which is not supplied in the ubuntu 5.06 (required for mysqli). 

I want to install some graphical libraries to php and i'm not sure if that method will allow me to do that. 

I'm confused about make in general. since there are so many makefile.in and makefile.am that do not do anything when you type "make".

---

### Post by BramWillemsen on 2009-03-01
sorry for the bumping but the post dropped to the second page again.

---

### Post by BramWillemsen on 2009-03-01
Sorry for the bump

---

### Post by BramWillemsen on 2009-03-01
It seems like ./configure does not create a makefile from makefile.in. There is no error message though when i use ./configure

edit: It finally works!!! it seems like it was missing the ncurses resource :) I apperantly didn't check the log from ./config well enough. I hope this will help others with the same problem

---

