---
title: "Easy PHP like program?"
date: 2009-02-18
forum: General Help
---

### Post by ELD on 2009-02-18
Basically on windows i can install a program called easy php which allows me to host php/mysql/phpmyadmin etc on my machine (so i can do offline web development).

How easy would it be to have something like that on ubuntu?

---

### Post by lykwydchykyn on 2009-02-18
Run "sudo tasksel" and check "LAMP server" then hit 'ok'.  I don't know if you have to install phpmyadmin seperately, but if so it's just:
```

sudo aptitude install phpmyadmin

```

---

### Post by ELD on 2009-02-18
> **lykwydchykyn said:**
> Run "sudo tasksel" and check "LAMP server" then hit 'ok'.  I don't know if you have to install phpmyadmin seperately, but if so it's just:
```

sudo aptitude install phpmyadmin

```

So doing that will enable everything i need?

---

### Post by lykwydchykyn on 2009-02-18
> **ELD said:**
> So doing that will enable everything i need?

I don't know; what all do you need?  Sorry, I've never used easy PHP, so I don't know what all is included.

It will install apache, php, mysql, and the necessary packages to get them all working together.  It should be configured out of the box, just put your php files in /var/www and they should work.

---

### Post by fragos on 2009-02-18
After installing LAMP you have one small bit of configuration to do. Put the following 3 lines in /etc/apache2/httpd.conf.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

They will instruct apache to process PHP code. I've never installed phpmyadmin. Store your site in development in /var/www and when you enter localhost as the location for the browser you'll be accessing the internal WEB server that will run PHP.

---

