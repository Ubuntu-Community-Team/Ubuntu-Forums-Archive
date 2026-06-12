---
title: "PHP pages opens in Gedit"
date: 2006-02-13
forum: Desktop Environments
---

### Post by ClickHeRe on 2006-02-13
I just upgraded my PHP5 installation to 5.1.2 and now the PHP pages are downloaded and opened in Gedit instead of being displayed.

I checked the apache2.conf and mime.types file which have the correct application/php entries

libapache2-mod-php5 is installed also.

anybody got a clue on this. Pages worked fine when it was PHP 5.0.5 before!

Thanks

David

---

### Post by alfotis on 2006-02-13
sounds like add application line to me 

try adding AddType-applixation/app-httpd-php or something in apache.conf

(You'll find the exact line in the installation README for php)

---

### Post by ClickHeRe on 2006-02-14
I already have this in my apache2.conf file

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

and they are also in the /etc/mime.types

so that is probably not the problem.

---

### Post by schmidty on 2006-02-19
I have tried everything including adding to apache.conf:

AddHandler x-httpd-php .php

But nothing seems to work...

any ideas from anyone let me know!

Schmidty

---

