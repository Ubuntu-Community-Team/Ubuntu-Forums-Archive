---
title: "[SOLVED] PHP not opening"
date: 2008-12-29
forum: General Help
---

### Post by sirschuster on 2008-12-29
So here's my problem, when i attempt to run a php file, its does this thing were it asks where i want to save it.

But... I do have php, apache, and mysql installed, and it still does that. If i type in localhost into my browser it says, "It works!". No it doesnt!

What can i do to fix this, i mut be missing the boat somewhere. I'm running Ubuntu Ibex.

Thanks!

---

### Post by eBoxNet on 2008-12-29
> **sirschuster said:**
> If i type in localhost into my browser it says, "It works!". No it doesnt!


apache works not sure if your php works,try to make a file called info.php and add inside ```
<?php phpinfo(); ?>
```
put htis on your httpdocs (or public_html or whatever you call the apache root folder ) folder and open [http://127.0.0.1/info.php](http://127.0.0.1/info.php) on your web browser

if you c your php and apache informations then it really works if not then you haven't setup php module for apache.

---

### Post by sirschuster on 2008-12-29
Thanks. Nope, doesnt run. So how do I set-up a php module?

---

### Post by Agent ME on 2008-12-29
Have you installed the '[libapache2-mod-php5](apt:libapache2-mod-php5)' package?

---

### Post by sirschuster on 2008-12-29
Yes I have.

---

### Post by sirschuster on 2008-12-29
Using Rapache, it shows that apache is running, as well as my php5 module.

Clickin on the module shows... [PHP]<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>[/PHP]

---

