---
title: "apache won't parse php files"
date: 2005-05-27
forum: Desktop Environments
---

### Post by red herring on 2005-05-27
I'm trying to set up phpgroupware to be shared by a number of local users. I have apache2 and mod-php4 installed just as the package dependencies would have them. /etc/apache2/mods-enabled contains symlinks to php4.load and php4.conf in /etc/apache2/mods-available (this is the default, I haven't changed anything). But when I point my browser to [http://localhost/phpgroupware/admin](http://localhost/phpgroupware/admin), the php files aren't parsed & executed, just downloaded by the web-browser.

I'm sure its some very simple thing I forgot to do ... can anyone help? Thanks

---

### Post by shakin on 2005-05-27
did you restart Apache?

```

$ sudo /etc/init.d/apache2 restart

```

Also make sure the right PHP packages are installed. For Apache 2 this is:

libapache2-mod-php4
php4
php4-common

you'll also probably want php4-mysql and maybe php4-gd and a few others.

---

### Post by red herring on 2005-05-27
[QUOTE=shakin]did you restart Apache?
```

$ sudo /etc/init.d/apache2 restart

```[/QUOTE]
Done
[QUOTE=shakin]
libapache2-mod-php4
php4
php4-common[/QUOTE]

And done already. Still the same result. I tried clearing my browser's cache (?) but that has no effect. Thanks anyway, any other ideas?

---

