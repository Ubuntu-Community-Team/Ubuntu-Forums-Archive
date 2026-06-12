---
title: "Regexp help (fail2ban)"
date: 2009-04-18
forum: General Help
---

### Post by Per Olav on 2009-04-18
I'm trying to set up fail2ban to block vulnerability scanners. I can't seem to get the regexp right, because I can't get any mathces on this rule:

```
[Definition]
  
docroot = /var/www/
badadmin = PMA|phpmyadmin|myadmin|mysql|mysqladmin|sqladmin|mypma|admin|xampp|mysqldb|mydb|db|pmadb|phpmyadmin1|phpmyadmin2
failregex = [[]client <HOST>[]] File does not exist: 
ignoreregex =

```

And from the apache error log:

```
[Sat Apr 18 23:03:51 2009] [error] [client xx.xx.xx.xx] File does not exist: /var/www/xampp
```

---

