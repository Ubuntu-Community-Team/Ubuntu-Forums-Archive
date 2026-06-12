---
title: "First Linux Server, help with MySQL?"
date: 2005-07-24
forum: Desktop Environments
---

### Post by Mr.Rogers on 2005-07-24
Well, I've installed many distros of Linux and so far, Ubuntu is the only one I'm going to be using.

I want to use it to run Apache, PHP, MySQL, FTP Server and Mail server once complete. I usually do servers in Windows and am very new to Linux so please excuse my ignorance.

I've got Apache2, PHP 4 and MySQL 4.0.23 installed via apt-get. Apache and PHP seem to work, [http://www.infirasys.com/phpinfo.php](http://www.infirasys.com/phpinfo.php). The problem is with MySQL, I'm not sure where to start with it. I installed it like Apache and PHP and uncommented the correct line php.ini.

i do sometihng like this to login, my root password is already set

#mysql -u root -p
PASSWORD: <password>

Welcome to MySQL... yada yada


mysql>create database testdb;
-----------------------------------------------

Now that I created a test DB, I procede to see if Xoops works on it, I get pass all the install screens and when I click "Finish" I just get a blank white screen. PHPbb does this as well after click "Next" after filling in all of the DB infos and such. There aren't any errors or anything just blank white screens.

I had this issue under Windows once and corrected itsomehow but I've since forgotten and this is a whole new OS to me.

Also, where is the httpd.conf file? I found the one in /etc/apache2 but it only has about 5 lines or so in it?

Hope you guys can help, thanks!

---

### Post by DJ_Max on 2005-07-24
Did you install the *php4-mysql* package via apt-get?

---

### Post by Mr.Rogers on 2005-07-24
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4-mysql
#

 :?

---

### Post by DJ_Max on 2005-07-24
I thought it was called php4-mysql, but I'm not booted in Ubuntu. Umm, do a search
apt-cache search mysql

It should give list the package you're looking for.

It should have been there. [https://wiki.ubuntu.com/ApachePHPMySQL](https://wiki.ubuntu.com/ApachePHPMySQL)

---

### Post by DJ_Max on 2005-07-24
[QUOTE=DJ_Max]I thought it was called php4-mysql, but I'm not booted in Ubuntu. Umm, do a search
apt-cache search mysql

It should give list the package you're looking for.

It should have been there. [https://wiki.ubuntu.com/ApachePHPMySQL](https://wiki.ubuntu.com/ApachePHPMySQL)[/QUOTE]
 You probably don't have the repository it's in. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by Mr.Rogers on 2005-07-24
Thanks a million, I was wondering why that package wasn't installing as I tried before and just skipped it.

I installed it and Apache, PHP and MySQL seem to be working fine. Now to find a mail and FTP server!  :)

---

### Post by majikstreet on 2005-07-24
[QUOTE=Mr.Rogers]Thanks a million, I was wondering why that package wasn't installing as I tried before and just skipped it.

I installed it and Apache, PHP and MySQL seem to be working fine. Now to find a mail and FTP server!  :)[/QUOTE]
 I know you weren't asking a question, but here are two links anyway:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)    <----- Mail server

[http://ubuntuguide.org/#installftpserver](http://ubuntuguide.org/#installftpserver)     <----- Ftp Server

---

