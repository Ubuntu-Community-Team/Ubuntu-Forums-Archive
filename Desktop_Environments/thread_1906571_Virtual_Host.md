---
title: "Virtual Host ?"
date: 2012-01-09
forum: Desktop Environments
---

### Post by fneurieser on 2012-01-09
Hello,

first of all I ask you to apologize my English. Second I'm a newbie to linux and ubuntu 11.10 is the first linux-product i installed on a virtualbox (surprise it works). 

but there is one thing I can't solve. I've installed apache2, mysql, php and phpmyadmin and when opening firefox and trying to launch localhost I get the message it works. So everythings works fine for me. But now I want to add some named virtual hosts and therefore I added the followings folders: 
a) /var/www/html/web229/html
b) /var/www/html/web652/html

and in /etc/apache2/sites-available I created the files web229 and web652 with the following settings:
```

<VirtualHost *>

   ServerAdmin admin@localhost
   ServerName web229
   DocumentRoot /var/www/html/web229/html/
   
   <Directory /var/www/html/web229/html/ >
        Option Indexes FollowSymlinks MultiViews
        AllowOverride None
        allow from all
   </Directory>

   ErrorLog /var/log/apache2/error.log
   LogLevel warn
   CustomLog /var/www/html/web229/log/access.log combined
   ServerSignature On
</VirtualHost>

```and 

```

<VirtualHost *>

   ServerAdmin admin@localhost
   ServerName web652
   DocumentRoot /var/www/html/web652/html/
   
   <Directory /var/www/html/web652/html/ >
        Option Indexes FollowSymlinks MultiViews
        AllowOverride None
        allow from all
   </Directory>

   ErrorLog /var/log/apache2/error.log
   LogLevel warn
   CustomLog /var/www/html/web652/log/access.log combined
   ServerSignature On
</VirtualHost>

```Of course I've added an index.php / index.html to each new site with different content.

But after restarting the apache and trying to launch localhost I get the content from site web229.

What did I wrong?

Any help  would be appreciated.

Regards
Franz-Georg

sorry, forgotton the hosts files located at /etc/hosts
```

127.0.0.1     localhost
127.0.0.1     web229
127.0.0.1     web652

```

---

