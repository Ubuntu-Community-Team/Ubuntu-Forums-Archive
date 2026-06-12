---
title: "Unable to setup phpmyadmin in 9.04"
date: 2009-05-29
forum: Desktop Environments
---

### Post by raunhar on 2009-05-29
I tried setting up Local Apache server with Phpmyadmin, but have been unsuccessful.
The following are showing as installed:
php5, apach2, mysql-client, mysql-server, libmysqlclient15-dev, php-mysql, phpmyadmin.

When I enter [http://localhost/](http://localhost/)
I get the following:Index of /
[ICO]	Name	Last modified	Size	Description
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80

On [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

The requested URL localhost/phpmyadmin/ was not found on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80

www folder under var is empty.

Please suggest how to get it done.

---

### Post by raunhar on 2009-05-30
Please help.
Previouslu using 8.10, no problems in localhost setup but did a mistake of doing a fresh install of 9.04 by formating 8.10.

Help Please or I will have to switch back to 8.10

---

### Post by mal on 2009-05-30
Raunhar,

I have phpmyadmin running on 9.04 Jaunty, so it should be possible for you.

The first message that you get when you browse to [http://localhost/](http://localhost/) is what you would expect when there is nothing in /var/www/.

I suggest you check that the phpmyadmin files are installed in /usr/share/phpmyadmin/.  If so, try creating a link:

```
$ sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```

This should do the trick.

Mal

---

### Post by raunhar on 2009-05-31
while installing phpmyadmin from terminal, getting the following message:
Setting up phpmyadmin (4:3.1.2-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
             the script did not pass --debconf-ok to ucf. The maintainer
             script should be fixed to not stop debconf before calling ucf,
             and pass it this parameter. For now, ucf will revert to using
             old-style, non-debconf prompting. Ugh!

             Please inform the package maintainer about this problem.
Replacing config file /etc/phpmyadmin/config-db.php with new version
dbconfig-common: flushing administrative password

---

### Post by ActiveFrost on 2009-05-31
Terminal :
```
sudo gedit /etc/apache2/apache2.conf
```
Add this line :
```
Include /etc/phpmyadmin/apache.conf
```
Restart Apache :
```
sudo /etc/init.d/apache2 restart
```

Let us know if it helps ;)

---

### Post by chrisod on 2009-06-04
Don't know about the OP but that worked for me. Thanks!

---

### Post by Tibuda on 2009-06-05
Guys, you should try the Mysql GUI tools. They are a lot better than phpmyadmin. The Linux version is available in the [mysql-gui-tools-common]("apt:mysql-gui-tools-common") package, and the Windows version is available in the official MySQL site.

---

