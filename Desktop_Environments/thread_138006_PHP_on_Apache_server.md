---
title: "PHP on Apache server"
date: 2006-03-01
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-03-01
Im running apache 2.0.54, and it works fine.

My problem is the php. I've installed php5 the best I can, but its obviously something wrong. Because when you click on a php file on the server, you are just being prompted to download it, the browser won't open it...??

And its not the browsers fault, cause it handles other php files just fine, on other servers..

So, howto configure apache with php?

---

### Post by gmclachl on 2006-03-01
Have you tried running 

  sudo a2enmod php (or php5) 

 George

---

### Post by stiankarlsen on 2006-03-01
I tried the following:

> 
stian@stian:~$ sudo a2enmod php
Password:
This module does not exist!
stian@stian:~$ sudo a2enmod php5
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
stian@stian:~$ sudo a2enmod php4
Module php4 installed; run /etc/init.d/apache2 force-reload to enable.
stian@stian:~$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server  (Apache2)...                                   Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load:
Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
                                                                         [fail]
stian@stian:~$


But its seems to be returning with errors all over the place. Howto fix this?



edit:
Managed to fix it, thanks man, what you said seems to have helped. At first, it broke a package on my system, but when I fixed it, php files load fine.

thanks again..

stian

---

### Post by gmclachl on 2006-03-01
You can't run 2 versions of PHP (well you can but it needs tinkering with) 

 I am not an expert but i would try running 

 sudo a2dismod php5 
 sudo a2dismod php4 

 and then just enable php5
 
 sudo a2enmod php5 

George

---

