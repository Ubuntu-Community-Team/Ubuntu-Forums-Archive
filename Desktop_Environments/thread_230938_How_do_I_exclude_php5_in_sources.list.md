---
title: "How do I exclude php5 in sources.list"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Peter Mount on 2006-08-06
Hello

I installed LAMP for use with PHP4.x and MySQL4.x (with Apache 2) as per:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I had it working fine.

This morning it didn't work fine as it just asked me to save the php file to disk. I did a search for php5 on my hard drive and I found php5 directories even though I did a "sudo aptitude remove php5" and tried to reinstall php4 (plus I did "sudo a2enmod php4" after re-installing libapache2-mod-php4).

I'm guessing that when I did a "sudo aptitude upgrade" then the php5 directories must have been created. Could this be the cause of my problem?

How do I exclude php4 being upgraded to php5 in the sources.list? I had a similar situation in Fedora Core 5 but I haven't learned how to do the exclude of php5 in Kubuntu Dapper yet.

Thanks

---

### Post by az on 2006-08-06
The php5 package is a metapackage.  Removing it does not remove the other php5 packages.  The key is libapache2-mod-phpx

If you want apache2 to use php4, install libapache2-mod-php4.  Make sure you use the apache2 package and not apache (libapache-mod-php4).  You will have to get rid of libapache2-mod-php5.


You can remove all the php5 packages if you don't use php5.  They were not installed by the upgrade, you must have installed them at some point.

---

### Post by Peter Mount on 2006-08-07
Thanks azz

I have a feeling phpmyadmin installed the php5 files when I did:

"sudo aptitude install phpmyadmin"

I removed it and just used the phpMyAdmin-2.7.0-pl2.tar.gz file to install phpmyadmin, 

So far it all seems to be working OK. I'll see how it goes. I suppose I should try the latest version of phpmyadmin from the downloads at [www.phpmyadmin.net](www.phpmyadmin.net) but I'm happy to use whatever works.

Have fun

---

