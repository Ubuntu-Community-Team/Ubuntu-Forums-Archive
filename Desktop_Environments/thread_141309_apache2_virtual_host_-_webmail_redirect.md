---
title: "apache2 virtual host - webmail redirect"
date: 2006-03-08
forum: Desktop Environments
---

### Post by rendyr on 2006-03-08
I have not been able to find this answer anywhere....this proablem has actually plagued me since apache 1.3 days.....very frustrating!

Simple explanation:

ubuntu breezy
apache2

I have apache2 running website:   blah.com   just fine under /www/blah (docroot)

...I have installed a webmail client (in /www/webmail)

PROBLEM:  Cannot set up apache to send visitors who go to webmail.blah.com to /www/webmail   They are always sent only to /www/blah

I can understand how to do this if the domainnames were different, but all requests for webmail.blah.com  never resolve to docroot at /www/webmail, they always resolve to docroot at /www/blah

I want this set up in this way because I will eventually have foo.com and funny.com (examples) to also access the one instance of webmail as well (webmail.foo.com, webmail.funny.com), and I do not want to install it once for every domain.

If apache2 sites-enabled entry for "blah"  is removed, webmail comes up fine (not DNS issue, etc.)

....This is just a problem, I think, of having the machine name "webmail" (from webmail.blah.com) not resolve to its own docroot because the webserver thinks that everything is handled by the main webserver running at blah.com

...is this indeed handled by two different sites-available entries, or do I need to add something into the blah file to "rewrite" that specific webmail address to go to another docroot?

please help.......thanks for any advice

---

### Post by banadushi on 2006-03-08
In your virtual host directive put:

```

Alias /webmail /www/webmail

```

Now any request that starts with /webmail will be served out of the /www/webmail directory.

Have a good one!

Jason

---

### Post by banadushi on 2006-03-08
Ha,  it would help if i read your post closer!

Ok, so you need to configure another virtual host.  In your httpd.conf put:

```

NameVirtualHost 192.168.1.1
<VirtualHost 192.168.1.1>
ServerName webmail.blah.com
ServerAlias webmail.foo.com
ServerAlias webmail.bar.com

DocumentRoot /www/webmail
ErrorLog /www/Logs/webmail_error
CustomLog /www/Logs/webmail_access combined
</VirtualHost>

```

Replace 192.168.1.1 with whatever IP you want to serve content on.  You can put as many ServerAlias fields as you want to server out on.

Have a good one!

Jason

---

### Post by rendyr on 2006-03-08
I actually have that, I think...  It seems as if the virtualhost for blah.com is not allowing the separate virtualhost entry for webmail.blah.com to exist.  

Is not the very use of "httpd.conf" changed in the latest version of apache?

I look at the httpd.conf file and it has some mention about it being there only for backwards compatibility.  So, I have three entries in the sites-available (linked to enabled).  "default" "blah" and "webmail"

"blah" shows up all the time, redirecting any requests for webmail to the docroot of "blah"

if blah is disabled, then webmail works just fine......How would I get this to work with the new apache2 format of sites-available/enabled?

contents of blah:

# NameVirtualHost *
<VirtualHost flibberty.com>
        ServerName [www.blah.com](www.blah.com)
        ServerAlias blah.com
       
        DocumentRoot /www/blah/ROOT/
        <Directory /mmedia/www/flibberty/>
                Options Indexes FollowSymLinks MultiViews
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>



contents of webmail

<VirtualHost *>
ServerName webmail.blah.com
DocumentRoot /www/webmail/
<Directory /www/webmail/>
 Options Indexes FollowSymLinks MultiViews
 AllowOverride AuthConfig
 Order allow,deny
 allow from all
</Directory>
ErrorLog /var/log/apache2/error-webmail.log
LogLevel warn
CustomLog /var/log/apache2/access-webmail.log combined
ServerSignature On
</VirtualHost>

---

### Post by banadushi on 2006-03-08
The problem is that the Virtual hosting is not setup correctly.

NameVirtualHost is commented out.  This either needs to be activated as is or activated with your ip address, the difference is wether you want to virtualhost on all IP's or just a few.

You also are using mixed vhost entries.  This is bad and were apache is getting confused.  Lets assume that you are hosting these sites both on the IP of 192.168.1.10. This is what it should look like:

```

NameVirtualHost 192.168.1.10
<VirtualHost 192.168.1.10>
        ServerName www.blah.com
        ServerAlias blah.com
       
        DocumentRoot /www/blah/ROOT/
        <Directory /mmedia/www/flibberty/>
                Options Indexes FollowSymLinks MultiViews
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

<VirtualHost 192.168.1.10>
        ServerName webmail.blah.com
        DocumentRoot /www/webmail/
        <Directory /www/webmail/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all
        </Directory>
        ErrorLog /var/log/apache2/error-webmail.log
        LogLevel warn
        CustomLog /var/log/apache2/access-webmail.log combined
        ServerSignature On
</VirtualHost>

```

What this does is first tells apache is you are virtual hosting on 192.168.1.1.  Then it defines 2 virtual hosts on that IP address, each virtual host cliams a ServerName to answer to and posibbly a ServerAlias to answer to.

I'm not sure how Ubuntu bastardizes naming apache's conf files, most distros totally screw it up and make it a nightmare to troubleshoot or work with.  Apache itself still uses httpd.conf as the conf file, but that can be overridden at compile time to be something else.

Have a good one!

Jason

---

### Post by rendyr on 2006-03-08
HOORAY!  That fixed it indeed!  Instead of using two sites in the sites-enabled/active directory, just putting in those two entries into the one blah file did the trick!

thanks so much!   hooray

nick

---

