---
title: "You don't have permission to access"
date: 2009-03-23
forum: General Help
---

### Post by zayzet on 2009-03-23
I use my computer to use LAMP webserver. Then install and configure Moodle. Register domain name free on Dyndns.org. NAT router on port 80 connection is completed. They stand outside the internet to access this site, the receipt of the notice as follows. Hope you help me as well as familiar with the new linux and Moodle. Thank!

[I][B]Forbidden
You don't have permission to access /moodle on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch Server at nhatruong.dyndns.org Port 80[/B][/I]

---

### Post by wineman on 2009-03-23
you have an issue with your apache2 .htaccess config. you probably just need to setup apache2's security permissions for that folder.

dude there was this massive example of .htaccess file, but copy (or edit) the .htaccess in /var/www and add a directory listing with the following:
(Save this file as ../moodle/.htaccess, **with the old .htaccess file backed up**)
```

# This file provides access to the server from anywhere.
# Comment to deactivate.

Order Deny,Allow
Allow from all
Allow from 127.0.0.1
#Deny from all

# To allow execution of cgi scripts in this directory uncomment next two lines.

AddHandler cgi-script .pl .cgi
Options +ExecCGI



```
This example should work except that you might have an issue with denying permissions. (#Deny from all)

Good luck mate

---

