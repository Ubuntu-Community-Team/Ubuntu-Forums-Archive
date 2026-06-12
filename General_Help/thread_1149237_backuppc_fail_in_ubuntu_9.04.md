---
title: "backuppc fail in ubuntu 9.04"
date: 2009-05-05
forum: General Help
---

### Post by odror on 2009-05-05
I have just installed for the first time backuppc on my 64 mythbuntu 9.04.

The installation went well.,

But when I went to the web page
[http://MyPC/backuppc](http://MyPC/backuppc)

I get the following error:

> Forbidden

You don't have permission to access /backuppc on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_ssl/2.2.11 OpenSSL/0.9.8g Server at moriel.dror Port 80

In the appache2 error log I get
> [Mon May 04 22:10:25 2009] [error] [client 127.0.1.1] client denied by server configuration: /usr/share/backuppc/cgi-bin/


I do not know if it is related but when I restart apache2 I get:
>  * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

This did not used to be before the backup pc installation.

I do not have problem with other apache clients, horde2, squirrelmail and mythweb

---

