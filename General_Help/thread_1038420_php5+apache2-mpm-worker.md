---
title: "php5+apache2-mpm-worker"
date: 2009-01-12
forum: General Help
---

### Post by kkruecke on 2009-01-12
The article _[Installing Apache2 and PHP5 using mod_fcgid]("http://tinyurl.com/6jed8u")_ shows how to run php5 with apache2-mpm-worker. The advanage of apache2-mpm-worker over apache2-mpm-prefork is better performance.

1. Install apache2-mpm-worker and the fastcgi apache module libapache-mod-fcid
```
#apt-get install apache2-mpm-worker  libapache2-mod-fcgid
```

2. Enable the Fastcgi apache module **mod_fcgid**
```
#sudo a2enmod fcgid
```

3. Install **php5-cgi** and the command-line version **php5-cli**

```
#sudo aptitude install php5-cgi php5-cli
```

4. Add the following to **/etc/apache2/httpd.conf** or create a file in /etc/apache2/conf.d called, say, **/etc/apache2/conf.d/00-myconf**

```
<Directory /var/www>
AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php

# The line below is optional. You can add the ExecCGI option to each
# <Directory /var/www/some-path></Directory> block instead.

Options +ExecCGI
</Directory>

```

This is also a good place to add any Aliases you have
```

Alias /aptitude        /usr/share/doc/aptitude/html/en
Alias /apt             /usr/share/doc/apt-doc
Alias /phpgedview      /usr/share/phpgedview

<Directory /usr/share>
AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php
Options ExecCGI FollowSymlinks Indexes 
</Directory>
```

5. Then, for each virtual host configuration file you have in /etc/apache2/sites-available, add **ExecCGI** within a <Directoy /path-to-site> block (placed within your <VirtualHost> block). For example,  

#cat /etc/apache2/sites-availabe/yourdomain.com

```

<VirtualHost *:80>
ServerAdmin youremail@yourdomain.com
ServerName yoursite.tld
ServerAlias www.yourdomain.tld *.yourdomain.tld

DocumentRoot /var/www/yourdomain.com

ErrorLog        /var/log/apache2/yourdomain.tld-error.log
CustomLog       /var/log/apache2/yourdomain.tld-access.log combined

<Directory /var/www/yourdomain.com>
Options +ExecCGI 

AllowOverride All
Order Allow,Deny
allow from all
</Directory>
LogLevel warn
ServerSignature On
</VirtualHost>
```

Note: The **ExecCGI** was turned on in /etc/apache2/sites-available/default for /var/www and its subdirectories, so it is not strictly necessary within the <VirtualHost > block shown here. Using + adds fastcgi support (for php) to the options in force. Options don't merge with prior options (they replace them) unless + is used. You can specify entirely different Options, but you must include **ExecCGI**, if you want php support for your virtual host.

6. Enable your virtual host

```
#sudo a2ensite yourdomain.com
```

7. And reload the apache configuration

```
#sudo /etc/init.d/apache2 force-reload
```

or just restart apache2

```
#sudo /etc/init.d/apache2 restart
```

A similar technique is shown in this _[article]("http://tinyurl.com/7wblr6")_ from Digital Nerds

---

