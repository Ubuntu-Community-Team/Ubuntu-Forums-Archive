---
title: "Self Hosting Linux Domain Name QQQuestion"
date: 2009-02-07
forum: General Help
---

### Post by sjl127 on 2009-02-07
I can't seem to get apache2 to work with wordpress correctly, with virtual hosting...

On my host box, I have mysite.com hosted in a virtual host directory, /var/www/mysite with nothing in the /var/www.

All seems to work fine on the host box, but not from outside my network.  ???

---

### Post by sjl127 on 2009-02-07
When I'm outside my lan, and go to mysite.com or [www.mysite.com](www.mysite.com), it puts me into my server

/var/www directory (of which I have nothing), 

not my /var/www/mysite directory.


:(

---

### Post by sjl127 on 2009-02-07
I&#8217;ve searched everywhere and could not find a clear-cut way to configure Apache 2&#8217;s new design for linux for virtual hosting.

Let my trial-and-error help you have an easier time configuring your set-up.

My initial problems were learning how the old httpd.conf differed from the new apache2.conf with the addition of the new folders, sites-available and sites-enabled folders for virtual hosting.

When I found some other references and configured as told, when I would go to one of my sites, it would put me into my /var/www/ directory, which of course, has nothing in it except my two website folders.

Here&#8217;s how it worked for me.

I have two website that I host through one IP address.   This is my hosting directory structure:

/var/www/     contains no files and two folders:

/var/www/mysiteone
and
/var/www/mysitetwo

my    /etc/apache2/apache2.conf      contains nothing new, I did not touch it.

my   ./etc/apache2/sites-available/mysite1dotcom                contains:

```
    # FILE /etc/apache2/sites-available/mysite1dotcom

    NameVirtualHost *:80

    <VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName mysite1dotcom.com
    DocumentRoot /var/www/mysite1dotcom/
    <Directory />
    Options FollowSymLinks
    AllowOverride None
    </Directory>
    <Directory /var/www/mysite1dotcom/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory &#8220;/usr/lib/cgi-bin&#8221;>
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

    Alias /doc/ &#8220;/usr/share/doc/&#8221;
    <Directory &#8220;/usr/share/doc/&#8221;>
    Options Indexes MultiViews FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
    Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    </VirtualHost>
```

The important things are at the very top of this file:

```
NameVirtualHost *:80
<VirtualHost *:80>
```

This is what each of your virtual host site files should say.  *:80

All I did was copy the &#8216;default&#8217; file in my sites-available folder, pasted it twice and renaming them mysite1dotcom and mysite2dotcom.

Edit them, and make the necessary changes and additions:

```
    [COLOR="Red"]# FILE NEW VIRTUAL HOST FILE FOR MYSITE1DOTCOM

    NameVirtualHost *:80

    <VirtualHost *:80>[/COLOR]
    ServerAdmin webmaster@localhost

[COLOR="Red"]    DocumentRoot /var/www/[/COLOR]
    <Directory />
    Options FollowSymLinks
    AllowOverride None
    </Directory>
[COLOR="Red"]    <Directory /var/www/>[/COLOR]
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory &#8220;/usr/lib/cgi-bin&#8221;>
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

    Alias /doc/ &#8220;/usr/share/doc/&#8221;
    <Directory &#8220;/usr/share/doc/&#8221;>
    Options Indexes MultiViews FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
    Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    </VirtualHost>
```

What&#8217;s in RED are either additions or changes.

Then I created a link to these files in sites-enabled, restarted apache, and it works.

I hope this helps!

---

