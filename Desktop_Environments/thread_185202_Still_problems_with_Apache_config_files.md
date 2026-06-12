---
title: "Still problems with Apache config files"
date: 2006-05-31
forum: Desktop Environments
---

### Post by goneskiing on 2006-05-31
1) Did a fresh install of Apache 2 - now PHP files are being displayed as text instead of running as php. I have run a2enmod php5 and mod shows in mods-enabled.  Same old problem but I cannot remember or find the fix.

2) Apache will not reload without errors:
$ sudo /etc/init.d/apache2 force-reload
* Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

$ /etc/init.d/apache2 reload * Reloading apache 2.0 configuration... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by thasheep on 2006-05-31
The first error message on start isn't an error message at all. It's just saying you haven't set up your server with a registered domain name. Unless you have (ie you own goneskiing.com or whatever), there's nothing to worry about.
The second error is just because you're trying to start the initscript as your normal user, not root.
As for the php files, do they have the extension .php?

---

### Post by goneskiing on 2006-05-31
re server name - I'm just trying to run this as localhost.  I'll try changing ports.conf (I had done that before reinstalling) but time is the issue now.

---

### Post by thasheep on 2006-05-31
If your running it as localhost (127.0.0.1), it isn't an error so don't worry about it. Just remember to call the initscript with sudo (or set it to start at boot)

---

### Post by henriquemaia on 2006-05-31
[quote=goneskiing]1) Did a fresh install of Apache 2 - now PHP files are being displayed as text instead of running as php. I have run a2enmod php5 and mod shows in mods-enabled.  Same old problem but I cannot remember or find the fix.

2) Apache will not reload without errors:
$ sudo /etc/init.d/apache2 force-reload
* Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

$ /etc/init.d/apache2 reload * Reloading apache 2.0 configuration... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs[/quote]

About the first issue, to make that message disappear, you just have to add the directive 

[B]ServerName localhost

[/B]to you /etc/apache2/apache2.conf.

Like this (an excerpt of the beginning of that file):

# Based upon the NCSA server configuration files originally by Rob McCool.
# Changed extensively for the Debian package by Daniel Stone <daniel@sfarc.net>
# and also by Thom May <thom@debian.org>.

# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation
# (available at <URL:http://www.apache.org/docs/mod/core.html#lockfile>);
# you will save yourself a lot of trouble.

**ServerName localhost**

ServerRoot "/etc/apache2"

---

