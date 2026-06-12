---
title: "Locally resolving domain"
date: 2009-01-11
forum: General Help
---

### Post by Seena on 2009-01-11
Hello ,

I have installed Ubuntu in my local system started working .
Ubuntu forum seems to be very helpful for solving issue . So I thought of registering to this forum . Now my issue

I have installed Apache , Mysql , php and bind.
I wanted to create a domain for eg "test.com" which should resolve locally.
I wanted to set the local system as the domain's dns also wanted to create virtual host entry .

Please explain me step by step .

Thanks in advance 

Have a great day

---

### Post by linux_tech on 2009-01-11
Hi Seena, Welcome!


This explains how to setup dns using bind-
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

[http://www.debianadmin.com/creating-name-based-and-ip-based-virtual-hosts-in-apache.html](http://www.debianadmin.com/creating-name-based-and-ip-based-virtual-hosts-in-apache.html)

For server requests there is a Server Platforms category that 
will generate the most responses for server related questions:p

---

### Post by alenis on 2009-01-11
Putting a line such as

```
127.0.0.1 www.test.com
```

in the /etc/hosts file should solve your first problem.

To enable virtual hosts in apache I did the following:

1) edit apache2.conf adding at the bottom:

```

NameVirtualHost *:80 
<IfModule mod_ssl.c> 
    NameVirtualHost *:443 
</IfModule> 

```

2) configure the virtual sites creating in the /etc/apache2/sites-available directory a configuration file for each of them. Afterwards, you have to enable each virtual site with the command  a2ensite so that at the next start apache will read its configuration file.
In default.conf, which you will find in the sites-available directory, the only change needed is 
the deletion of the line:

```
NameVirtualHost *
```

To add another site, create a configuration file such as:

```

<VirtualHost *:80> 

  # Admin email, Server Name (domain name) and any aliases 
  ServerAdmin webmaster@test.com 
  ServerName  www.test.com

  # Index file and Document Root (where the public files are located) 
 
  DocumentRoot <insert correct path here>
  DirectoryIndex index.html # you can change this

  # Custom log file locations 
  LogLevel warn 
  ErrorLog  <insert correct path here>error.log 
  CustomLog <insert correct path here>access.log combined 

</VirtualHost> 

```

3) After a configuration change, you should (probably: maybe not all of thiese steps are necessary) stop apache, disable and enable the virtual site, and start apache again.
Corresponding commands are:

```

/etc/init.d/apache2 stop 

a2dissite <virtualhostname>

a2ensite <virtualhostname>

/etc/init.d/apache2 start 

```

where virtualhostname is the name of the configuration file of the virtual site you want to test.
Hope this helps.

---

