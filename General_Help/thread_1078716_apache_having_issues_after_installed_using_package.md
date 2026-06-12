---
title: "apache having issues after installed using package manager"
date: 2009-02-23
forum: General Help
---

### Post by barraymian on 2009-02-23
hi all,

so i installed apache2 and php5 using the following commands

```
    sudo apt-get install apache2

    sudo apt-get install php5

    sudo apt-get install libapache2-mod-php5


```

then i used the following command to start apache

```
    sudo /etc/init.d/apache2 restart
```

I should also mention that i had to go update apache2.conf file and add the following line in the end of the file otherwise i was getting error about 0.0.0.0:80 server address

```
ServerName localhost:80
```

my document root is /var/www/ (I don't know where this setting is, it used to be in httpd.conf file but apache2.conf seems to have replaced httpd.conf file and DocumentRoot is not in apache2.conf). I read it somewhere that /var/www becomes DocumentRoot

File permission on www directory is drwxrwxrw-
the owner is myusername and groupowner is "apache" which i created and myusername is part of the "apache" group

Now when i enter [http://localhost](http://localhost) in browser, i get the following error message

```
Forbidden

You don't have permission to access / on this server.
Apache/2.2.9 (Ubuntu) Server at localhost Port 80
```

Any insights into this will be greatly appreciated

thanks

---

### Post by Coreigh on 2009-02-23
I think you want your servername to be %h (default host name) or another defined name, and then make sure your /etc/hosts file points to 127.0.0.1 for localhost and the computers network name (and any other alias you want to refer to the local computer as.

Did you get any notices or alerts when you restarted Apache?

example hosts file
> 
127.0.0.1    localhost
127.0.0.1    myserver
127.0.0.1    myserver.mydomain.org
127.0.0.1    foo.mydomain.org


Since these are all pointing to the local IP they could all be on one line separated by spaces, but multi-lines works too and this is how you would do it if you had a public static IP like an actual www server.

---

