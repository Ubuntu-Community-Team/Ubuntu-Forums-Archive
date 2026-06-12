---
title: "Process  .html files as PHP"
date: 2011-01-27
forum: Desktop Environments
---

### Post by dldeskins on 2011-01-27
Hi,

I am running Ubuntu 10.10 64 bit to do testing for a web site. I have successfully added a .htaccess file to the production site to process .html files as PHP files, but cannot get my localhost to process the files the same way.

Addition to apache2.config:
[HTML]
<Directory "/home/*/public_html/*">
	AllowOverride All
	Order Deny,Allow
	Allow from all
</Directory>
[/HTML]

The .htaccess file
[HTML]
AddType application/x-httpd-php5 .htm .html .php .blog .comment .inc
DirectoryIndex index.php index.html index.htm 
[/HTML]

When the file is called, the server attempts a download.

---

### Post by dldeskins on 2011-01-28
anyone?

---

### Post by asmoore82 on 2011-01-28
Have you installed and set up mod_php?

---

### Post by dldeskins on 2011-01-28
> **asmoore82 said:**
> Have you installed and set up mod_php?

I have the standard install, so yes, mod_php5 is installed.

---

### Post by SeijiSensei on 2011-01-28
> **dldeskins said:**
> ```

AddType application/x-httpd-php5 .htm .html .php .blog .comment .inc
DirectoryIndex index.php index.html index.htm 

```

Add the AddType directive to the /etc/apache2/mods-enabled/mime.conf file, and edit the DirectoryIndex entry in /etc/apache2/mods-enabled/dir.conf to your liking.  Restart Apache with "sudo service apache2 restart".  Now these directives will be the defaults for all virtual servers unless they're specifically overridden in a <VirtualHost> configuration or in .htaccess.

---

### Post by dldeskins on 2011-01-29
> **SeijiSensei said:**
> Add the AddType directive to the /etc/apache2/mods-enabled/mime.conf file, and edit the DirectoryIndex entry in /etc/apache2/mods-enabled/dir.conf to your liking.  Restart Apache with "sudo service apache2 restart".  Now these directives will be the defaults for all virtual servers unless they're specifically overridden in a <VirtualHost> configuration or in .htaccess.

This did not work.

---

### Post by SeijiSensei on 2011-01-29
Hmm.  Well, having looked more closely at /etc/apache2/mods-enabled/php5.conf, it appears you need to make some changes there as well.

You'll notice that public_html is specifically excluded from PHP processing by default.  If that's the directory that's causing your problems, you need to re-enable PHP.

---

### Post by dldeskins on 2011-01-29
> **SeijiSensei said:**
> Hmm.  Well, having looked more closely at /etc/apache2/mods-enabled/php5.conf, it appears you need to make some changes there as well.

You'll notice that public_html is specifically excluded from PHP processing by default.  If that's the directory that's causing your problems, you need to re-enable PHP.

I set the FileHandler in /etc/apache2/mods-enabled/php5.conf and got it to work. I would have really preferred to do it through .htaccess, but I suppose this will do until I get my work done.

Thanks!

---

