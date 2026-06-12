---
title: "Controlling Error Reporting in PHP (9.04)"
date: 2009-05-16
forum: General Help
---

### Post by slipstream180 on 2009-05-16
Hi All - I'm having a similar problem as that reported in [http://ubuntuforums.org/showthread.php?t=1042086](http://ubuntuforums.org/showthread.php?t=1042086). 

I was running PHP on MAC OS X v10.5, and then moved my PHP code over to Ubuntu 9.04. I diff'd my old (Mac) php.ini against my new (Ubuntu) php.ini to get an identical setup. 

Even though display_errors = Off, in the php.ini file, I'm still getting errors reported in the browser. 

Other php.ini settings:
error_reporting = E_ALL
log_errors=On
error_log = /var/log/php_error

Likewise, most PHP errors & warnings get reported in the apache /var/log/apache2/error.log file. I've checked the permissions on this file and they belong to root:adm w/ -rw- r-- --- file permissions. 

Very few errors get into php_error. It's permissions are root:root -rw- r-- r--. I figure these permissions must be ok, because the file was originally created by apache. (I assume)

Running phpinfo() from the webroot dir confirms that display_errors=Off.

Strangely, it's only one kind of error that gets reported in the browser. (When a variable points to a non-existent path)

Not sure what else to do here.

Appreciated any help or ideas to figure this one out...

---

### Post by LoneWolfJack on 2009-05-16
maybe you are activating errors from within your script?

---

### Post by slipstream180 on 2009-05-16
Good idea LoneWolfJack. grep'd my scripts against 'error_reporting' and 'display_errors'. Nothing there...

I'm stumped. Maybe there's some setting in apache, that's affecting reports into the browser...? Will investigate.

---

