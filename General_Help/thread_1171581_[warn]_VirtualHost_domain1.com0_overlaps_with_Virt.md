---
title: "[warn] VirtualHost domain1.com:0 overlaps with VirtualHost..."
date: 2009-05-27
forum: General Help
---

### Post by Peabo on 2009-05-27
I've been smashing my face against this for a few days now, can't seem to get it working. Ive tried replacing IP addresses with * and a variety of other things, with no avail.  Any assistance provided would be much appreciated. 

Error message:

[warn] VirtualHost domain1.com:0 overlaps with VirtualHost domain2.com:0, the first has precedence, perhaps you need a NameVirtualHost directive

----------------

etc/apache2/httpd.conf

NameVirtualHost (IP):80

<VirtualHost (IP):80>
ServerName [www.domain1.com]("http://www.domain1.com")
ServerAlias domain1.com *.domain1.com
DocumentRoot /home/user/public_html/domain1.com/public/
</VirtualHost>

<VirtualHost (IP):80>
Servername [www.domain2.com]("http://www.domain2.com")
ServerAlias domain2.com *.domain2.com
DocumentRoot /home/user/public_html/domain2.com/public/
</VirtualHost>

-------------------------

/etc/apache2/sites-enabled/000-default


<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/user/public_html/domain1.com/public/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

-------------------------------

/etc/apache2/sites-enabled/domain1.com.conf

# Domain: domain1.com
# Public: /home/user/public_html/domain1.com/public

<Virtualhost domain1.com>

ServerAdmin [EMAIL="webmaster@domain1.com"]webmaster@domain1.com[/EMAIL]
ServerName [www.domain1.com]("http://www.domain1.com")
ServerAlias domain1.com *.domain1.com
DirectoryIndex index.html
DocumentRoot /home/user/public_html/grindstoneforge.com/public/

LogLevel warn
ErrorLog /home/user/public_html/domain1.com/log/error.log
CustomLog /home/user/public_html/domain1.com/log/access.log combined

</Virtualhost>

-------

/etc/apache2/sites-enabled/domain2.com.conf

<Virtualhost domain2.com>

ServerAdmin [EMAIL="webmaster@domain1.com"]webmaster@domain1.com[/EMAIL]
ServerName [www.domain2.com]("http://www.domain2.com")
ServerAlias domain2.com *.domain2.com
DirectoryIndex index.html
DocumentRoot /home/user/public_html/domain2.com/public/

LogLevel warn
ErrorLog /home/user/public_html/domain2.com/log/error.log
CustomLog /home/user/public_html/domain2.com/log/access.log combined

</Virtualhost>

---------------------

I would be happy to provide any other files, just let me know which ones.

Thank you in advance for any help any of you can provide!

---

### Post by Peabo on 2009-05-27
/bump

Halp!

---

### Post by Barriehie on 2009-05-29
I've got the same issue!  When my days off roll around I'll see what I can do.

Barrie

---

### Post by Barriehie on 2009-05-30
Try this:

```

etc/apache2/httpd.conf

NameVirtualHost (IP):80

<VirtualHost :*>
ServerName [www.domain1.com]("http://www.domain1.com/")
ServerAlias domain1.com *.domain1.com
DocumentRoot /home/user/public_html/domain1.com/public/
</VirtualHost>

<VirtualHost :*>
Servername [www.domain2.com]("http://www.domain2.com/")
ServerAlias domain2.com *.domain2.com
DocumentRoot /home/user/public_html/domain2.com/public/
</VirtualHost>

```Actually what I would do also is have [www.domainX.com.conf]("http://www.domainX.com.conf") in /etc/apache2/sites-available and then enable domainX.com via a2ensite.  i.e. none of this in httpd.conf.

Barrie

---

