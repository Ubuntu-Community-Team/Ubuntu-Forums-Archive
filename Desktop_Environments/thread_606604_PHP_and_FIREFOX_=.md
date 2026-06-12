---
title: "PHP and FIREFOX = ?"
date: 2007-11-08
forum: Desktop Environments
---

### Post by ixlam on 2007-11-08
Im running Gusty 7.1 and updated everything.

Firefox wants to download php pages instead of opening them.

I have all the libs.and php packages installed my website works fine just the php pages don't.
I'm almost certain this is a Firefox issue but i could be wrong. Ive checked the links and made a "test.php" page and get the same results.

what do I do?

---

### Post by MRiGnS on 2007-11-08
If this forum works, php is working for...

The site you're trying to access may has a problem with its own webserver.

---

### Post by ixlam on 2007-11-08
how to fix the server then?...
im using Apache2 2. how do I enable scripts or add  idex.php  ?

I do have  these installed>
php5
libapache2-mod-php5
php5-cig
php5-common
php5-mysql
apache2.2-common
lib-apache2-mod-php5

thanks in advance!

---

### Post by MRiGnS on 2007-11-08
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by az on 2007-11-08
Reload the page using CTRL-F5.  That will clear the cache.  Sometimes that can be the problem.

---

### Post by Ferio on 2007-11-12
Thank God I'm not the only man on Earth with this problem. Yes, it happens to me too, and it happens in Firefox 2, Firefox 3 and Opera, so it may be an Ubuntu problem. The thing is that sometimes it works fine, but most of the time pages will ask to download index.php, or won't post at all (it has just happened to me at another forum when trying to do it). I'll try the cache-cleaning method, but I'd like to fix this problem.

Thank you in advance.

---

### Post by jaschahal on 2007-11-12
Hey guys,

Just check your httpd.conf file and check if there is a php handler for apache.
You should be looking for somthing like this

**LoadModule php5_module        modules/libphp5.so # mandatory**

[COLOR="DarkRed"]#[optional]
*[/COLOR]AddHandler php5-script php  # sometimes on linus this is just a requirement*
[COLOR="DarkRed"]# [OR][/COLOR]
*AddHandler application/x-httpd-php .php *


# Add index.php to your DirectoryIndex line:
DirectoryIndex index.html index.php

AddType text/html       php # if you want to parse html files as php

just try it, i think you should be fine, you need to be sure that libphp5.so is present

jas

---

### Post by Ferio on 2007-11-13
Thanks, jaschahal, but as I've said before it's not an Apache problem; sometimes I can post here at Ubuntu Forums and sometimes I can't; it's the same with [http://forum.textpattern.com](http://forum.textpattern.com), 
and with my blog ([http://www.tecniferio.com](http://www.tecniferio.com)), that uses Textpattern CMS and which is, to tell the truth, my real concern since I'm paying for the hosting service. I suppose it'll be exactly the same with every PHP-powered site that requires posting in a way or another.

I don't know why or how, but it's an Ubuntu problem this one we have here.

---

### Post by Ferio on 2007-11-13
Thing is getting worst, I can't even access my Last.FM account; I'll try to post about this odd behaviour in some PHP forum, and maybe in some browser forum, just to see if they have any idea...

What I can't say is why it lets me post in here...

---

### Post by jaschahal on 2007-11-13
Ok the problem is not with apache or php not being configured properly. Its the mime_type configuration file that may be causing proble

can you actually try to remove php mime from /etc/mime_typeXX file

comment all the lines that have something like this application/xxxxx .php .phps

and then try to clear the cache.

if you are access say index.php as [http://localhost/index.php](http://localhost/index.php) try to append any random number in query string for example [http://localhost/index.php?23948](http://localhost/index.php?23948)

i hope that may be usefule

jaschahal

---

### Post by Ferio on 2007-11-13
No, it didn't worked. The lines I commented were these (/etc/mime.types):
```

application/x-httpd-php                phtml pht php
application/x-httpd-php-source            phps
application/x-httpd-php3            php3
application/x-httpd-php3-preprocessed        php3p
application/x-httpd-php4            php4

```
I think my blog uses PHP 5, could this be the reason? Not having a specific handler, I mean.

---

