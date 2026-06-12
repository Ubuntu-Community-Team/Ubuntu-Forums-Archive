---
title: "PHP installed but not working"
date: 2005-11-13
forum: Desktop Environments
---

### Post by theboatashore on 2005-11-13
Hi there

I've installed Apache2 and PHP5 on my laptop to develop sites offline.  The usual question posted seems to be that the browser tries to download the .php file.  I don't have that problem.  My issue is that when I point the browser to the testphp.php file in /var/www it displays a blank page.  No error messages and no attempt to download.  When an .html page is displayed that contains a PHP include, the includes are left out and the rest of the page displayed perfectly.

I've been trawling the forums for a few days now and have attempted (what seems to be) every fix suggested.  I don't know what else to try.  Ultimately, all I want is to be able to use PHP includes on my site.  Right now it seems too much trouble for something so simple :(

Thanks for your time,
Michael

---

### Post by kelsey23 on 2005-11-13
Type:

$php /var/www/testphp.php

And see what happens. If it gives an error, then PHP in not installed correctly. Otherwise, you do not have PHP configured for Apache.

---

### Post by theboatashore on 2005-11-13
Hi there

I got this error message after typing *$php /var/www/testphp.php*:

/var/www/testphp.php: line 1: syntax error near unexpected token `('
/var/www/testphp.php: line 1: `<?php phpinfo(); ?>'

Thanks,
Michael

---

### Post by theboatashore on 2005-11-13
After playing around with a few more settings, I now have the same problem as everyone else...namely, my browser tries to download the .php file.

---

### Post by drummer on 2005-11-13
Is it not working for any php files? maybe the apache module mod_php isn't installed or enabled.

EDIT - *sudo nano /etc/apache/httpd.conf* then find this line at the end and uncomment it: *#Include /ect/apache/mod_php.conf* and restart apache.
This may not be exactly right as this is on my server running Slackware and might be a little different.

---

### Post by theboatashore on 2005-11-13
Hi

*libapache2-mod-php5* is installed, if that's what you mean.  It's also enabled.

All .php files are now provoking a request to download them.

---

### Post by drummer on 2005-11-13
hmm... I edited my post to include what I did to enable php on my apache install. For me the module was installed but not enabled in httpd.conf, and I had my browser trying to download the php files.. maybe just a coincidence then

---

### Post by theboatashore on 2005-11-13
I don't have the file you mentioned (/etc/apache/httpd.conf)...maybe because I'm running Apache2?  Not sure if this makes a difference.

---

### Post by drummer on 2005-11-13
probably, but it should be something similar. Have a look round in /etc for anything with httpd or apache2

---

### Post by theboatashore on 2005-11-13
This is the content of my */etc/apache2/httpd.conf* file:

[FONT="Arial"]# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so[/FONT]

Just checked my */etc/apache2/mods-enabled* folder and saw that php5.load and php5.conf are not there.  I remember checking on that a few hours ago and they were.  I may have changed something between now and then.  How can I be sure that php mods are enabled?

---

### Post by drummer on 2005-11-13
as per my above edit - find this line at the end and uncomment it: *#Include /ect/apache2/mod_php.conf* and restart apache.

And again, mod_php.conf might be called something different, have a look around /etc/apache2

---

### Post by theboatashore on 2005-11-13
Hey man

I tried those suggestions and still no goodness.  I've gotta bail now but I appreciate your time.  Thanks.

---

### Post by Stereotypical Rage on 2005-11-14
PHP5 wasn't working for me. My browser kept wanting to download it as a phtml file. Sure enough, I cleared my cache and it worked.:p

---

### Post by theboatashore on 2005-11-14
Thanks to all for the assistance, although it was something else entirely.  Still not sure what I did, but I came across a command that went something like this (I can't find where I found it):

*sudo /etc/init.d/apache2/force-reload*

After running that, testphp.php loaded fine, as well as all my PHP includes.  I still don't know what that command does.

Oh well, thanks to all who replied to my questions.  I do appreciate your time and effort.

---

