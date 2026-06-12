---
title: "phpmyadmin problem"
date: 2009-01-19
forum: Desktop Environments
---

### Post by raunhar on 2009-01-19
I installed phpmyadmin, but when I try to open [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

A pop up opens which has the following instaructions:
You have chosed to open .. which is a :PHTML file from [http://localhost](http://localhost)

What should Firefox do with this file?
Open/Save


What should be done, so that the page opens up properly.

Pl. suggest.

---

### Post by mcduck on 2009-01-19
First, try clearing your browser's cache.

If that doesn't do the trick run these commands to make sure PHP is enabled in Apache:
```
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
```

---

### Post by raunhar on 2009-01-19
sudo a2enmod php5  says php5 module not installed. I checked through Synaptic Manager. PHP5 was installed. 
apache2 is the server.
Is there any other thing to be installed.

---

### Post by mcduck on 2009-01-19
You'll need at least "libapache2-mod-php5".

The best way to install the whole LAMP stack is to run "sudo tasksel install lamp-server". That will make sure you get everything required.

It's amazing why so many guides choose the more complicated way of apt-getting every required package separately (probably simply because the authors don't know about tasksel)..

---

