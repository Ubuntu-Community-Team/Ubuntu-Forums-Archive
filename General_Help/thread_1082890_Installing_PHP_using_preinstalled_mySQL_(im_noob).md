---
title: "Installing PHP using preinstalled mySQL (im noob)"
date: 2009-02-28
forum: General Help
---

### Post by BramWillemsen on 2009-02-28
Hello everyone.

A few days ago i purchased a laptop. I directly installed ubuntu, but i'm not that good with Linux yet. I have been reading a book about php and mysql for some time, and i'd like to test some of my newly acquired skills. The specific book that I use gives a guide to install mysql and php with apache and such in Linux. Yesterday i tried to install mysql 5.1 but i ran into some trouble because 5.0.6 was already installed on my computer.S This messed up mysql completely so i removed all mysql and used the apt-get install feature to get 5.0.6 back. MySQL works now perfectly (when i know more about linux ill try to boost it to 5.1), but i do have problems when i want to install php.

The specific book I'm using (Luke Welling, Laura Thomson ->"PHP and MYSQL Web Development") told install php in the following way.

Download the php tar.gz file. Go with the terminal to the directory where you untarred it. Then use the following command:

./configure --prefix=/your/path/to/php \
--with-mysqli=/your/path/to/mysql_config \
--with blabla \
--with blabla

The problem is that i don't have a mysql_config file on my computer to link to. I guess i really need this for the mysqli feature. How did you guys install php on your computer? I'm using the 8.10 desktop 64 bit edition btw. Do i have to uninstall mysql 5.0.6 again to install 5.1 in some way to get the mysql_config file? Or is there something that i forget ? I'm totally new to Linux so i may have made some mistake. Thanks a lot for the help.

kind regards,

Bram Willemsen

---

### Post by BramWillemsen on 2009-02-28
bump

---

### Post by mckenna1977 on 2009-02-28
This worked for me...

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by BramWillemsen on 2009-02-28
Thanks for the suggesting. I looked through and it explained quite a few things, but i prefer to get mysql 5.1.31 installed the normal way first. I downloaded the "Compressed GNU TAR archive (tar.gz)" from the source tab. Then i follow this guide.

[http://dev.mysql.com/doc/refman/5.1/en/quick-install.html](http://dev.mysql.com/doc/refman/5.1/en/quick-install.html)

the step that tells me to do "make" fails, because it says there is no makefile for some reason. there is a makefile.am and makefile.in though, but for some reason make does not do anything. It says: "No targets specified and no makefile found. Stop."

Am i doing something wrong? I am logged in as root and i am in the mysql directory (the ./config part worked fine). Make just fails for some reason.

---

### Post by BramWillemsen on 2009-02-28
I have no clue what's going wrong. i followed the guide literally.

---

