---
title: "change /var/www directory in apache2"
date: 2009-03-14
forum: General Help
---

### Post by artheus on 2009-03-14
Hey!

How do I change from the default '/var/www' directory to eg. '/mnt/sdb1/www'?

I just can't find the place to config that..

Cheers

---

### Post by igor. on 2009-03-14
You could either edit /etc/apache2/httpd.conf and add:
```
DocumentRoot /mnt/sdb1/www
```

---

### Post by Iowan on 2009-03-14
> **igor. said:**
> You could either edit /etc/apache2/httpd.conf and add:
```
DocumentRoot /mnt/sdb1/www
```
or...? ;)

As I recall, that is covered in [here.]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by artheus on 2009-03-14
Thank you!:D

---

