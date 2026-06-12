---
title: "How to access installed software"
date: 2010-06-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raac on 2010-06-10
Hi, I have a question, I've been looking for PHP for linux, and I found out that I would be able to install it with the command

apt-get install libapache2-mod-php5

Now I'm trying to find an icon or something to click in order to open it, but I can't find one.  Where does it go when you install it?? I would appreciate some help here. (I'm new with linux)

Thanks

---

### Post by binary10 on 2010-06-10
As you've installed it via the apt-get install, have you tried to create a php file in /var/www/ just as test ?

create a hello.php

and put in that file something like:


> <? phpinfo(); ?>

and then using firefox: [http://localhost/hello.php](http://localhost/hello.php)

---

