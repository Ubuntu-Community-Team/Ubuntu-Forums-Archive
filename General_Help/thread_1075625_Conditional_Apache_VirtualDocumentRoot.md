---
title: "Conditional Apache VirtualDocumentRoot"
date: 2009-02-20
forum: General Help
---

### Post by filburt1 on 2009-02-20
I administer the Ubuntu 8.04 64-bit server used by our office for web development. People's web roots reside on their own desktops as shares, and the server mounts each web root ("sandbox") and magically creates VirtualHosts for each person based on the project name; for example, foo.bar.domain.com accesses the "foo" project on "bar"'s sandbox.

This is what I have now, which works fine:

```
<Directory /mnt/sandboxes>
	Options FollowSymLinks +ExecCGI

	AllowOverride All
	Order allow,deny
	Allow from all
	
	EnableMMAP Off
	EnableSendFile Off
</Directory>

<VirtualHost *:80>
	ServerName sandboxes.domain.com
	ServerAlias *.*.domain.com

	UseCanonicalName Off

	Alias /magic_errors /var/www/errors
	VirtualDocumentRoot /mnt/sandboxes/%2/%1/httpdocs/app/webroot

	EnableMMAP Off
	EnableSendFile Off

	ErrorDocument 403 /magic_errors/sandbox_403.php
	ErrorDocument 404 /magic_errors/sandbox_404.php
</VirtualHost>
```

The problem is that most, but not all, of our projects are based off CakePHP, which suggests using the directory app/webroot as the DocumentRoot. So, how can I append "/app/webroot" to VirtualDocumentRoot if such a directory exists for a given request, and leave it alone otherwise?

---

### Post by kidders on 2009-02-21
Hi there,

Sounds like a job for a RewriteRule. You could create a RewriteCond that checks whether app/webroot is a directory & a rule to append it to the document root.

---

