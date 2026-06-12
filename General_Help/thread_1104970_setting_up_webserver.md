---
title: "setting up webserver"
date: 2009-03-24
forum: General Help
---

### Post by happyhacker on 2009-03-24
I already have apache2 installed, I think it was for webmin or  SSH server. In webmin I cannot see apache under servers even though it is shown in running processes. Is there a reason for this?

My real query is I want to run a webserver with PHP, MYSQL and PHPMyAdmin, etc. Because I have apache already how should I install the others needed as I assume I cannot install the LAMP as an install?

---

### Post by Cheesemill on 2009-03-24
You can just run the following to install the rest of the packages, it will just skip over any that are already installed.

```
sudo apt-get update && sudo apt-get -y install lamp-server^
```

Cheesemill

---

### Post by happyhacker on 2009-03-24
OK, thanks. Is that little caret "^" on the end of your instruction supposed to be there?

---

### Post by Cheesemill on 2009-03-24
Yup, it sure is.

---

### Post by happyhacker on 2009-04-01
Well I did that from the webmin command shell and I see that mysql and apache are running processes but PHP is not there and if I make a testphp.php and put it in var/www and access it from my PC browser [http://192.168.0.2/testphp.php](http://192.168.0.2/testphp.php) I get a 404 page.

I would also like to install phpmyadmin but when I do a "sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin" the screen asks me if I want to continue and I can't as it does not allow me to type in! Is there a modification to that command which install without asking for permission to continue?

So far have not got a LAMP system running.

---

