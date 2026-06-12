---
title: "Accessing my files from a browser"
date: 2009-01-06
forum: General Help
---

### Post by quikone8 on 2009-01-06
I am installing Wordpress. For some reason I cannot access the wordpress file from my browser. I have wordpress installed in /var/www/wordpress. I can browse to the ip or any of my url's, but I cannot access wordpress or /var/www/wordpress or wp-admin. I can't figure out why, I assume it has to do with ownership and/or permissions.

Anyone have suggestions for me?

---

### Post by Barriehie on 2009-01-07
So what are the permissions of the files in /var/www/wordpress ???

Barrie

---

### Post by quikone8 on 2009-01-07
How do I find out?

---

### Post by jerome1232 on 2009-01-07
the directory
```
ls -ld /var/www/wordpress
```

the files
```
ls -l /var/www/wordpress
```

---

### Post by quikone8 on 2009-01-07
> **jerome1232 said:**
> the directory
```
ls -ld /var/www/wordpress
```

the files
```
ls -l /var/www/wordpress
```

drwxrwxrwx 5 root root 4096 2009-01-05 18:36 /var/www/wordpress

---

### Post by quikone8 on 2009-01-07
> **quikone8 said:**
> drwxrwxrwx 5 root root 4096 2009-01-05 18:36 /var/www/wordpress

total 288
-rwxrwxrwx 1 root root   397 2008-05-25 14:33 index.php
-rwxrwxrwx 1 root root 15410 2008-12-06 00:47 license.txt
-rwxrwxrwx 1 root root  7638 2008-10-29 13:10 readme.html
drwxrwxrwx 7 root root  4096 2008-12-10 15:49 wp-admin
-rwxrwxrwx 1 root root 40271 2008-11-28 14:04 wp-app.php
-rwxrwxrwx 1 root root   220 2008-10-14 00:22 wp-atom.php
-rwxrwxrwx 1 root root   274 2008-05-25 09:50 wp-blog-header.php
-rwxrwxrwx 1 root root  3424 2008-11-18 23:58 wp-comments-post.php
-rwxrwxrwx 1 root root   238 2008-10-14 00:22 wp-commentsrss2.php
-rwxrwxrwx 1 root root  2618 2009-01-05 18:58 wp-config.php
-rwxrwxrwx 1 root root  2496 2008-12-07 14:31 wp-config-sample.php
drwxrwxrwx 4 root root  4096 2008-12-10 15:49 wp-content
-rwxrwxrwx 1 root root  1242 2008-09-18 01:09 wp-cron.php
-rwxrwxrwx 1 root root   220 2008-10-14 00:22 wp-feed.php
drwxrwxrwx 5 root root  4096 2008-12-10 15:49 wp-includes
-rwxrwxrwx 1 root root  1986 2008-05-25 09:50 wp-links-opml.php
-rwxrwxrwx 1 root root  2004 2008-10-31 13:24 wp-load.php
-rwxrwxrwx 1 root root 19738 2008-12-03 12:04 wp-login.php
-rwxrwxrwx 1 root root  6932 2008-12-09 11:03 wp-mail.php
-rwxrwxrwx 1 root root   487 2008-05-25 09:50 wp-pass.php
-rwxrwxrwx 1 root root   218 2008-10-14 00:22 wp-rdf.php
-rwxrwxrwx 1 root root   316 2008-05-25 09:50 wp-register.php
-rwxrwxrwx 1 root root   220 2008-10-14 00:22 wp-rss2.php
-rwxrwxrwx 1 root root   218 2008-10-14 00:22 wp-rss.php
-rwxrwxrwx 1 root root 18285 2008-11-10 11:54 wp-settings.php
-rwxrwxrwx 1 root root  3434 2008-05-25 09:50 wp-trackback.php
-rwxrwxrwx 1 root root 92514 2008-12-09 11:03 xmlrpc.php

---

### Post by hwttdz on 2009-01-07
How are you trying to access it, it should work like 

file:///var/www/wordpress/index.php (just put this in firefox's address bar)

of course note that you're not viewing it through a webserver. Getting a webserver up and going is a different thing (but very doable, even to beginners).

---

### Post by stillboy on 2009-01-07
How did you install? Did you download from the wordpress site? Do you have Apache2, Mysql, PHP, etc. packages installed, if not

```
sudo apt-get install apache2 mysql-server php5
```

If you do have the full Apache, MySQL, PHP setup installed, make sure that your apache is running, you might want to restart using 

```
sudo /etc/init.d/apache2 restart
```

What happens when you pull up [http://localhost](http://localhost) in your browser (from you linux box) ? do you see anything?

---

### Post by stillboy on 2009-01-07
> **hwttdz said:**
> How are you trying to access it, it should work like 

file:///var/www/wordpress/index.php (just put this in firefox's address bar)

of course note that you're not viewing it through a webserver. Getting a webserver up and going is a different thing (but very doable, even to beginners).

That will not work for a php/server based application - php is interpreted by the server (apache) and must be accessed through [http://serveraddress/wordpress/index.php](http://serveraddress/wordpress/index.php)

That method will work fine for html files, but not php, python, ruby, etc - those have to use the server backend to access the database and run the interpreter.

---

### Post by hwttdz on 2009-01-07
> **stillboy said:**
> That will not work for a php/server based application - php is interpreted by the server (apache) and must be accessed through [http://serveraddress/wordpress/index.php](http://serveraddress/wordpress/index.php)

That method will work fine for html files, but not php, python, ruby, etc - those have to use the server backend to access the database and run the interpreter.

Well you can view php... files, they just won't render in the way that you might expect, i.e. you view raw code. Of course I figured as you did that the user might be interested in viewing through a webserver, hence the disclaimer that that method is viewing the file not through a webserver.

---

