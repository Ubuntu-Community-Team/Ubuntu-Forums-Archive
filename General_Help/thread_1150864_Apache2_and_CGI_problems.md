---
title: "Apache2 and CGI problems"
date: 2009-05-06
forum: General Help
---

### Post by Urema on 2009-05-06
Hi,

I set up apache2 in order to run cgi-scripts.
I ran all my programs elsewhere and everything was fine.
Ran them here....and i get the cgi-scripts opening in a web browser rather than executing.
So i reassigned all the permissions so the scripts are executable...
.....i still get the same thing.

Does anyone know of a good site for help, or know what to do here? 

Thanks in advance

N Dean G.

---

### Post by cariboo on 2009-05-06
Have you had a look at this [Apache-cgi howto]("http://httpd.apache.org/docs/1.3/howto/cgi.html")?

---

### Post by Urema on 2009-05-08
Doesn't seem to be doing much different....but thanks anyway!

I've been through shed-loads of forums about this, and none seem to help at all. 

I've even removed Apache, PHP etc.....re-installed them just in case there was a problem initially, and still nothing.

Confusion is word.

N Dean G.

---

### Post by fragos on 2009-05-09
The LAMP install (Apache, MySQL and PHP) requires a bit of configuration to run PHP code. The file to be edited is /etc/apache2/httpd.conf. If it's already there it's probably empty, if not create it. Place the following three lines in it. The

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

The web server will have to restart for the configuration changes to take effect. The next time your sytem boots will do that or run the following CLI.

sudo /etc/init.d/apache2 restart

---

