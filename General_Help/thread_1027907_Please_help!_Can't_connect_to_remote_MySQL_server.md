---
title: "Please help! Can't connect to remote MySQL server"
date: 2009-01-01
forum: General Help
---

### Post by Gwaihirjp on 2009-01-01
What I am trying to do is to write a webpage that connects to a remote MySQL server (not localhost) from my Ubuntu desktop. I'v successfully installed Apache2 and PHP5, and managed to get PHP working locally in the /var/www folder.
So today I attempted to connect to the database with this code:

$db=mysql_connect("servername","username","password");

And when I tested the webpage with Firefox this is what came back:

Warning: mysql_connect() [function.mysql-connect]: Can't connect to MySQL server on 'servername' (4) in /var/www/test/test.php on line 61

I know for sure that the servername, username and password are correct. When I use PHPmyadmin on the host server I can log in to the same database without a problem. I've installed the MySQL extension for PHP5 by editing my php.ini file, so that's not the problem either. I'm really stuck now and don't know where else to go for help.

Does anyone have an idea what I may be doing wrong? I would really like to solve this as soon as possible so any help would be highly appreciated.

EDIT: Oh and I've just realized.. when I load the php webpage it takes an awfully long time to load, and it says "waiting for localhost" at the bottom. Wonder why it says "localhost" when it's not?

---

### Post by afbase on 2009-01-01
is your ubuntu desktop behind a router?

---

### Post by Gwaihirjp on 2009-01-02
> **afbase said:**
> is your ubuntu desktop behind a router?
Yes, it's a wired LAN connection through a router and a hub.

---

