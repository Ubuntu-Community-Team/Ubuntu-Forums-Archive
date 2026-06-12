---
title: "can't find php on filesystem after install"
date: 2009-04-12
forum: General Help
---

### Post by timmè on 2009-04-12
hi
iv installed apache + php + mysql on my system and all works well.
but if i try to debug a php script in Komodo it says it can't find the php interpreter...
where can i find it in my file system?
thx

---

### Post by Linteg on 2009-04-12
Make sure that that the command-line interpreter (e.g. php5-cli) is installed.

---

### Post by timmè on 2009-04-12
how can i install it? im a total noob with linux.

thanks

---

### Post by timmè on 2009-04-12
sudo apt-get install -f php5-cli is what i did.
but where is the executable?
i need to specify that path in komodo

---

### Post by vk_rams on 2009-04-12
If you install apache2 automatically php will be installed in /etc/apache2/php. I will give you a detailed list of installation commands of php,mysql

sudo apt-get install apache2
sudo apt-get install mysql-server
sudo apt-get install php5-mysql

This will solve your issue

---

### Post by Linteg on 2009-04-12
> **timmè said:**
> sudo apt-get install -f php5-cli is what i did.
but where is the executable?
i need to specify that path in komodo
Good, the path to the executable should be /usr/bin/php

---

### Post by timmè on 2009-04-12
thx but now i have the following problem regarding php.ini files
->PHP debugging configuration failed: unable to copy [etc/php5/cli/php.ini] 
to [etc/php5/apache2/php.ini]
any idea?
im used using zend on window, but i cant install it on ubuntu :(

---

### Post by timmè on 2009-04-12
ok, fixed it, im just a dumbass...:)

---

### Post by vk_rams on 2009-04-13
Thats good to hear... :)

---

