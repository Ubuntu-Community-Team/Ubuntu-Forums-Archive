---
title: "Can't access localhost"
date: 2020-04-25
forum: Desktop Environments
---

### Post by geomcd1949 on 2020-04-25
Upgraded from 18.04 to 20.04. Since, can't access localhost.

&#9679; apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2020-04-24 17:12:45 EDT; 24h ago
       Docs: [https://httpd.apache.org/docs/2.4/](https://httpd.apache.org/docs/2.4/)

Apr 24 17:12:45 george-desktop systemd[1]: Starting The Apache HTTP Server...
Apr 24 17:12:45 george-desktop apachectl[1953]: apache2: Syntax error on line 146 of /etc/apache2/apache2.conf: Syntax error on line 3 of /etc/apache2/mods-enabled/php7.2.load: Cannot load /usr/lib/apache2/mod>
Apr 24 17:12:45 george-desktop apachectl[1908]: Action 'start' failed.
Apr 24 17:12:45 george-desktop apachectl[1908]: The Apache error log may have more information.
Apr 24 17:12:45 george-desktop systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
Apr 24 17:12:45 george-desktop systemd[1]: apache2.service: Failed with result 'exit-code'.
Apr 24 17:12:45 george-desktop systemd[1]: Failed to start The Apache HTTP Server.
~

This is the /etc/apache2/mods-enabled/php7.2.load file:

# Conflicts: php5
# Depends: mpm_prefork
LoadModule php7_module /usr/lib/apache2/modules/libphp7.2.so

Thanks!

---

### Post by TheFu on 2020-04-25
The Release Notes specify which Apache release and which Php is shipped with 20.04 server.   I&#8217;d start there since both have changed.  i'm pretty certain php 7.2 has been replaced.

---

