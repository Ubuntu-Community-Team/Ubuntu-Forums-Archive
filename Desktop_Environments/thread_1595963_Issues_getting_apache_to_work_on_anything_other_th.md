---
title: "Issues getting apache to work on anything other than port 80"
date: 2010-10-13
forum: Desktop Environments
---

### Post by juliushibert63 on 2010-10-13
I can't seem to get apache to work on a non default 80 port. 

I've got in to ports conf and changed it to the follwoing. 

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 55741

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>


```

I've also disabled firestarter to rule that out as well. As soon as the port is changed back to 80 I can access the server fine and I get the standard apache working file. 

Also when restarting apache via the terminal it works but I do get a few errors. 

```
/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
   ...done.

```

I'm running apache2 on Ubuntu10.4 64bit version. 

Any ideas what could be going wrong here.

---

### Post by wheredidrealitygo on 2010-10-13
Check your first three lines of the .conf you posted.

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
```

that file is just a pointer to /etc/apache2/sites-available/default

if you look in that file there's another port to change right at the top:

```
<VirtualHost *:80>
```

---

### Post by juliushibert63 on 2010-10-13
Thanks for your help.

Turns out as you suggested changing the /etc/apache2/sites-enabled/000-default file worked a treat.

---

### Post by wheredidrealitygo on 2010-10-13
Glad to hear it worked for you!

Please go to thread tools at the top and mark your thread as solved. :D

---

