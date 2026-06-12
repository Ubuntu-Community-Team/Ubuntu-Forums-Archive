---
title: "PHP 5.3 RC2 not reading settings from php.ini"
date: 2009-05-13
forum: General Help
---

### Post by TDK800 on 2009-05-13
- phpinfo says settings are read from /etc/php.ini

- Making changes to /etc/php.ini and restarting apache / rebooting server does not change the php settings in phpinfo.

- I've tried setting /etc/php.ini chmod to 777 and ownership to apache, root, local user, nothing affects the settings php uses. 



Solved:
There was comment ; missing from in front of this line in the default php.ini:
[http://www.php.net/manual/en/errorfunc.configuration.php#ini.track-errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.track-errors)
causing an error.

---

