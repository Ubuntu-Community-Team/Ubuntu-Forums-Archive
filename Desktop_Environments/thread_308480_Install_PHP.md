---
title: "Install PHP?"
date: 2006-11-28
forum: Desktop Environments
---

### Post by hraposo on 2006-11-28
I can not install PHP in edgy. I install the packages php5 and libapache2-mod-php5 but the php din't in install in apache.

---

### Post by FryerFox on 2006-11-28
Did you restart apache?

> sudo /etc/init.d/apache2 restart

---

### Post by hraposo on 2006-11-28
Yes

---

### Post by hraposo on 2006-11-28
I did: apt-get --purge remove apache2 php5 libapache2-mod-php5
and I delete de file apache2 in /etc/apache2
Now, when I try install apache the file /etc/apache2 and this contents don't appears no more? How can I solve this?

---

