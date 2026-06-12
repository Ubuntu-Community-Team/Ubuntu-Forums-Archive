---
title: "Dissapearing Folders While Password Protecting Apache"
date: 2009-01-08
forum: General Help
---

### Post by lrochon on 2009-01-08
Hi ok so here's my problem i hope this is the best place to post this:

I have installed an apache server and have changed my root directory so my site-available/default looks like this:

```

<VirtualHost *:8010>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/Azio
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/Azio>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	<Directory /media/Azio/Media/Ebooks>
		AllowOverride None
		Order Deny,Allow
		Deny from all
	</Directory>

	<Directory /media/Azio/Media/Itunes>
		AllowOverride None
		Order Deny,Allow
		Deny from all
	</Directory>

	<Directory /media/Azio/Media/Pictures>
		AllowOverride None
		Order Deny,Allow
		Deny from all
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

```

and it works great I can access the index.html file i wrote and click a link to see an index of the remaining folders that i haven't denied access to which are ereader, Programs and Video

```

<html>
<body style="background-color:tan">

<h1> Welcome to My Server</h1>

<a href=Media>
<img border="0" src="images/Enter-Button.jpg">
</a>
</p>

</body>
</html>

```

So my next Step is to obviously Password protect the site i created my .htpasswd file useing the command line and I placed a .htaccess file in the Media folder because i want the password box to pop up when i click the link

```

AuthUserFile /etc/apache2/.htpasswd
AuthType Basic
AuthName "My Media Server"
Require valid-user

```

and finally i change the

```

<Directory /media/Azio>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride None
	Order allow,deny
	allow from all
</Directory>

```

section of my default file to

```

<Directory /media/Azio>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride AuthConfig
	Order allow,deny
	allow from all
</Directory>

```

Now everthing works exactly like it should it asks for a valid password when i click the link and everything the only problem is that the video folder does not show up, just Ereader and Programs, but when I remove the authconfig line and put back in None it comes back 

I'm Very confused about this there's nothing special about the Video folder it has all the same permissions as the other two.

Any Help would be much Appreciated.
Thx

---

### Post by lrochon on 2009-01-08
Ok so i figured it out htaccess files are garbage, i moved my authconfig stuff to my default file and it works great.

```

<VirtualHost *:8010>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/Azio
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/Azio>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
	
	<Directory /media/Azio/Media>
		Options Indexes FollowSymLinks MultiViews		
		AllowOverride None
		Order Deny,Allow
		allow from all
		AuthUserFile /etc/apache2/.htpasswd
		AuthType Basic
		AuthName "My Media Server"
		Require valid-user
	</Directory>
	

	<Directory /media/Azio/Media/Ebooks>
		AllowOverride None
		Order Deny,Allow
		Deny from all
	</Directory>

	<Directory /media/Azio/Media/Itunes>
		AllowOverride None
		Order Deny,Allow
		Deny from all
	</Directory>

	<Directory /media/Azio/Media/Pictures>
		AllowOverride None
		Order Deny,Allow
		allow from all
		AuthUserFile /etc/apache2/.htpasswd
		AuthType Basic
		AuthName "My Media Server"
		Require user lrochon
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

```

---

