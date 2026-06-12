---
title: "Apache"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Ryan H on 2006-08-05
Out of the blue my local apache server stopped working. I get this error when trying to restart it:
>  * Forcing reload of apache 2.0 web server... [Fri Aug 04 18:33:07 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
[Fri Aug 04 18:33:07 2006] [warn] The Alias directive in /etc/apache2/apache2.conf at line 168 will probably never match because it overlaps an earlier Alias.
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 7023?) not running


The lines in the apache2.conf are > Alias /icons/ "/usr/share/apache2/icons/" And > Alias /error/ "/usr/share/apache2/error/"

When I comment them out I only get the error >  * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 7023?) not running

I don't know what to do seeing as I only tried to run a PHP script.

Any help would be awesome.

-Ryan H

---

