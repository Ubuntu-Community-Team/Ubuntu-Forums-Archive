---
title: "apache2 and cgi"
date: 2008-12-17
forum: General Help
---

### Post by oneadvent on 2008-12-17
I am trying to get a perl script to run in my apache2 install.

It keeps saying "403 Forbidden" I am trying to run it from the root directory, something like "www.domain.com/perl.pl" and I still get that. Other things are avail in that directory. I did a chmod 777 on it and still no go.

My config file that deals with this says: ```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
                Options +ExecCGI
        </Directory>
        <Directory /var/www/>
                AddHandler cgi-script .cgi .pl
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Does anyone have any ideas on this one?

Thanks in advance.

---

### Post by albinootje on 2008-12-17
> **oneadvent said:**
> I am trying to get a perl script to run in my apache2 install.

It keeps saying "403 Forbidden" I am trying to run it from the root directory
--- cut ---
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
                Options +ExecCGI
        </Directory>
        <Directory /var/www/>
                AddHandler cgi-script .cgi .pl
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


Did you check whether there's interesting details in the apache log files ?

And you're talking about "root directory", first i thought you meant the www-root as in /var/www but you have a / directory defined in the apache config.
Can you try without the "AllowOverride None" in that / section ?
And add the add handler for cgi in that section too.

And does this script or other scripts run well in the /usr/lib/cgi-bin/ ?
Does you script need to have www-data as owner ?

---

### Post by oneadvent on 2008-12-17
I dont know what counts as interesting:

```
[Tue Dec 16 23:10:00 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Tue Dec 16 23:10:01 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue Dec 16 23:10:02 2008] [notice] Apache/2.2.8 (Ubuntu) mod_perl/2.0.3 Perl/v5.8.8 configured -- resuming normal operations
[Wed Dec 17 00:10:00 2008] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 17 00:10:00 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_perl/2.0.3 Perl/v5.8.8 configured -- resuming normal operations
[Wed Dec 17 00:10:30 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Dec 17 00:10:33 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Dec 17 00:20:55 2008] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/perltest.pl
[Wed Dec 17 00:22:31 2008] [error] [client 127.0.0.1] File does not exist: /var/www/cgi-start
[Wed Dec 17 00:22:50 2008] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/perltest.pl
[Wed Dec 17 00:23:31 2008] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/perltest.pl
[Wed Dec 17 00:23:35 2008] [error] [client 127.0.0.1] attempt to invoke directory as script: /usr/lib/cgi-bin/
[Wed Dec 17 00:26:08 2008] [error] [client 127.0.0.1] attempt to invoke directory as script: /usr/lib/cgi-bin/
[Wed Dec 17 00:26:14 2008] [error] [client 127.0.0.1] script not found or unable to stat: /usr/lib/cgi-bin/index.html
[Wed Dec 17 00:33:08 2008] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 17 00:33:08 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_perl/2.0.3 Perl/v5.8.8 configured -- resuming normal operations
[Wed Dec 17 00:33:25 2008] [error] [client 127.0.0.1] (8)Exec format error: exec of '/usr/lib/cgi-bin/perltest.pl' failed
[Wed Dec 17 00:33:25 2008] [error] [client 127.0.0.1] Premature end of script headers: perltest.pl
[Wed Dec 17 00:33:37 2008] [error] [client 127.0.0.1] attempt to invoke directory as script: /usr/lib/cgi-bin/
[Wed Dec 17 00:48:10 2008] [error] [client 127.0.0.1] (8)Exec format error: exec of '/usr/lib/cgi-bin/perltest.pl' failed
[Wed Dec 17 00:48:10 2008] [error] [client 127.0.0.1] Premature end of script headers: perltest.pl
[Wed Dec 17 11:15:31 2008] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 17 11:15:31 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_perl/2.0.3 Perl/v5.8.8 configured -- resuming normal operations
[Wed Dec 17 18:14:18 2008] [error] [client 66.210.216.19] File does not exist: /var/www/cgi-start
[Wed Dec 17 18:14:27 2008] [error] [client 66.210.216.19] attempt to invoke directory as script: /usr/lib/cgi-bin/
[Wed Dec 17 18:26:43 2008] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 17 18:26:43 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_perl/2.0.3 Perl/v5.8.8 configured -- resuming normal operations
[Wed Dec 17 18:26:47 2008] [error] [client 66.210.216.19] attempt to invoke directory as script: /usr/lib/cgi-bin/
[Wed Dec 17 18:35:42 2008] [notice] SIGHUP received.  Attempting to restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 17 18:35:42 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch mod_perl/2.0.3 Perl/v5.8.8 configured -- resuming normal operations
[Wed Dec 17 18:36:06 2008] [error] [client 66.210.216.19] Options ExecCGI is off in this directory: /var/www/perltest.pl
[Wed Dec 17 18:39:13 2008] [error] [client 66.210.216.19] Options ExecCGI is off in this directory: /var/www/perltest.pl
[Wed Dec 17 21:38:38 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Dec 17 21:38:42 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
```

Okay, whew. I tried all those things and it still said forbidden. It was not owned by www-data before, is that who should own all of my pages?

Any other ideas?

---

### Post by albinootje on 2008-12-18
Interesting errors are :

> [Wed Dec 17 18:14:18 2008] [error] [client 66.210.216.19] File does not 
> exist: /var/www/cgi-start

> [Wed Dec 17 18:14:27 2008] [error] [client 66.210.216.19] attempt to 
> invoke directory as script: /usr/lib/cgi-bin/

> [Wed Dec 17 18:36:06 2008] [error] [client 66.210.216.19] Options ExecCGI 
> is off in this directory: /var/www/perltest.pl

You should check these, see why they're there, whether they're really relevant, and fix the ones which really need fixing.

---

### Post by oneadvent on 2008-12-18
> [Wed Dec 17 18:36:06 2008] [error] [client 66.210.216.19] Options ExecCGI
> is off in this directory: /var/www/perltest.pl

That is the most current error. The others were from 2pm, and that was when I changed some stuff...

How do I turn that on in my config file?

---

### Post by albinootje on 2008-12-18
> **oneadvent said:**
> > [Wed Dec 17 18:36:06 2008] [error] [client 66.210.216.19] Options ExecCGI
> is off in this directory: /var/www/perltest.pl

That is the most current error. The others were from 2pm, and that was when I changed some stuff...

How do I turn that on in my config file?

In my /etc/apache2/apache2.conf there's this (uncommented) :

AddHandler cgi-script .cgi

And in /etc/apache2/sites-enabled/000-default :

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride AuthConfig
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

So you need "Options ExecCGI" in the /var/www directory part.

Perhaps it makes sense to rename your script into perltest.cgi too ?

---

### Post by albinootje on 2008-12-18
By the way, my approach would be to test your testfile first in /usr/lib/cgi-bin/ and see whether it works there.
It makes things easier to debug imho.

---

### Post by oneadvent on 2008-12-18
I am still getting this:

```
[Thu Dec 18 12:07:23 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.pl
[Thu Dec 18 12:07:24 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.pl
[Thu Dec 18 12:07:25 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.pl
[Thu Dec 18 12:08:02 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.pl
[Thu Dec 18 12:08:03 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.pl
[Thu Dec 18 12:08:04 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.pl
[Thu Dec 18 12:08:06 2008] [error] [client 127.0.0.1] Options ExecCGI is off in this directory: /var/www/perlscript.cgi

```

and I changed my config file to:
```
	DocumentRoot /var/www/
	<Directory />
AddHandler cgi-script .cgi .pl
Options ExecCGI
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		AddHandler cgi-script .cgi .pl
		Options ExecCGI
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
```

Thanks for the replies so far.

---

### Post by albinootje on 2008-12-18
Here's a solved tread about the same thing :
[http://ubuntuforums.org/showthread.php?t=717047](http://ubuntuforums.org/showthread.php?t=717047)

---

