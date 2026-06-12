---
title: "Apache2 premission issue on jaunty (?)"
date: 2009-05-16
forum: General Help
---

### Post by yamagami on 2009-05-16
Hi All

I did a clean install with Jaunty and reinstalled all my development environment. I moved  apache2 conf file for one virtual host from the old apache configuration, created the symlink in sites-enabled, and although the default virtual host does work fine and shows me the "It Works" page when i go to [http://localhost](http://localhost), 
when I go to [http://myotherserver](http://myotherserver) (i have entry in hosts file) it gives me:

Forbidden

You don't have permission to access /index.html on this server. 

The code files in my home dir belong to me (harel:harel). I tried messing with their permissions too of course, but nothing helped. 

I played with permissions till kingdom come. I removed and reinstalled. i begged, cried, and screamed. nothing helped. 

So I come a-knocking here... Help anyone?? please?

Thanks!
Harel

My Setup:

/var/www/freecrm is a symlink to the source code, which is in my home dir, checked out of svn. 

my virtual host setup for that server:

NameVirtualHost freecrm
<VirtualHost freecrm>
	ServerName freecrm
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/freecrm/
	DirectoryIndex index.cfm index.html index.htm
       <Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/freecrm/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

---

### Post by yamagami on 2009-05-16
A few directories up the tree were missing permissions.... 
once set it started working..
duh...

---

### Post by paradigm2 on 2009-05-16
> **yamagami said:**
> A few directories up the tree were missing permissions.... 
once set it started working..
duh...

Don't feel bad, I find that 90% of my issues are something stupid like that as well. :)

---

