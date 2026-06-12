---
title: "Apache2 question"
date: 2010-10-17
forum: Desktop Environments
---

### Post by Zidaps on 2010-10-17
I am running Apache2 on Jaunty. the hd where apache is installed is small in capacity and its default directory is in /var/www so the index page is served from /var/www.

I have large videos stored on a separate hard drive /media/largedrive how can I link my webpage on /var/www to the content in /media/largedrive/openshare ??

Thus far I have tried the following (in terminal)

sudo a2ensite openshare
Enabling site openshare.
Run '/etc/init.d/apache2 reload' to activate new configuration!

sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Here is the config file I created in /etc/apache2/sites-available for 'openshare'

> 
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /media/largedrive/openshare
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /media/largedrive/openshare>
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
So far access to index.htm on /var/www still works. So I know I haven't messed up so far. Please let me know if you know of a way I can link/serve the data on this other largedrive hard-drive.

Thanks.

---

### Post by Barriehie on 2010-10-17
I'ld first fix the servername issue; put this in your /etc/apache2/apache2.conf:
```

ServerName MyServerName.Whatever
```

I don't ever put anything in my /var/www/ dir.  I've got symlinks in there pointing to the actual files.  So I'ld setup openshare with document root as /var/www and then just put a symlink in /var/www pointing to /media/largedrive/openshare.

```

ln -s /media/largedrive/openshare /var/www/
```

HTH

---

### Post by Zidaps on 2010-10-18
Works !!

Much thanks :)

Quick note to anyone else who may benefit from this thread - The directory and URL used IS case sensitive. so make sure you Caps are not ignored.

---

### Post by Barriehie on 2010-10-18
> **Zidaps said:**
> Works !!

Much thanks :)

Cool! :)

---

