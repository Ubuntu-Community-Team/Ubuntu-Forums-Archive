---
title: "Another virtual host pb with apache2"
date: 2013-08-08
forum: Desktop Environments
---

### Post by ndaval on 2013-08-08
Hi there
Don't get me wrong, I'm not another lazy guy who ask help before lookin for the solution.

I've read many threads, tried many things but I still have the same pb
I've installed apache2 which works fine.
I've configured a virtual host but it still render the default configuration. It's like my DocumentRoot is not set (which is not the case).

[SIZE=2][B]/etc/hosts
[/B][/SIZE]```

[SIZE=2][FONT=courier new]127.0.0.1    localhost
127.0.0.1    mysite.dev
...[/FONT][/SIZE]
```

[B]/etc/apache2/sites-available/mysite.conf
[/B]
```
<VirtualHost *:80>    ServerAdmin me@mysite.dev
    
    DocumentRoot /var/www/mysite/public
    
    ServerName mysite.dev
    ServerAlias *.mysite.dev
    
    
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/mysite/public>
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



```

Where [FONT=courier new]/var/www/mysite[FONT=verdana] [SIZE=2]is a[/SIZE] symlink to [FONT=courier new]/home/me/web/mysite[/FONT] where my html files are
[/FONT][/FONT]
The site has been enabled with a2ensite and it is the only one (the default is disabled) and, of course, I've reloaded apache

At this point, I don't know what I'm doing wrong

Any help would be much appreciated
Thank you

Nicolas

---

### Post by TheFu on 2013-08-08
What are the file and directory permissions? Is the user running apache2 allowed to view the files in ~/web/mysite/ AND all the way down the directory tree?

I've never used the **ServerAlias *.mysite.dev** option with a wildcard. Do the docs say that works?

Do the access and/or error logs have any helpful information? They almost always explain the issue perfectly, IME. *"Use the logs, Luke."*

BTW, it would be helpful if you could edit the original question and use "code" tags so whitespace is retained.

---

### Post by ndaval on 2013-08-08
Hi TheFu
Thx for your reply
To answer your questions:
- All directories have www-data as owner (even the parent one)
- Don't know for the wildcard but [www.mysite.dev]("http://www.mysite.dev") don't change anything
- access/error log are empty...

**apache2ctl -S **give this

```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this messageVirtualHost configuration:
*:80                   mysite.dev (/etc/apache2/sites-enabled/mysite.conf:1)
ServerRoot: "/etc/apache2"
Main DocumentRoot: "/var/www"
Main ErrorLog: "/var/log/apache2/error.log"
Mutex watchdog-callback: using_defaults
Mutex rewrite-map: using_defaults
Mutex default: dir="/var/lock/apache2" mechanism=fcntl 
Mutex mpm-accept: using_defaults
PidFile: "/var/run/apache2/apache2.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
User: name="www-data" id=33 not_used
Group: name="www-data" id=33 not_used
User: name="www-data" id=33 not_used
Group: name="www-data" id=33 not_used



```

--> The Main DocumentRoot is not correct

Nicolas

---

### Post by TheFu on 2013-08-08
Your HOME is owned by www-data? That seems odd.  It is the real location of the website on disk that needs those permissions. A softlink doesn't bypass any restrictive permissions. Anyway, if the DocRoot isn't correct, then you haven't reconfigured Apache to support virtualhosts properly yet.  Did you check the /etc/apache2 files to ensure they are virtualhost compatible already?  

Especially "ports.conf"? Mine has:
```
NameVirtualHost *:8181
Listen 8181
```

Then, inside each virtualhost file ...
```
<VirtualHost *:8181>
        ServerAdmin webmaster@localhost
        ServerName nepal.example.com
        DocumentRoot /export/www/vhosts/nepal.example.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /export/www/vhosts/nepal.example.com/ >
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                DirectoryIndex index.html
        </Directory>
.
.
.
</VirtualHost>
```

Does that make sense?   Don't worry about the 8181 port - I use a reverse proxy on port 80 to serve about 20 different websites, applications, hide the real server behind and to be able to block "bad requests".  I don't think having apache directly available on the internet is safe either.

Anyway, I hope a concrete example helps.

---

### Post by ndaval on 2013-08-08
THANK YOU
You made my day :)

I've added NameVirtualHost *:80 in ports.conf and it works --> I didn't find this tip in any thread
To tell you the whole story, my apache worked perfectly with vhost (and I didn't touch the ports.conf file) but got broken after an (automatic) update
I finally ended up removing and reinstalling apache...
My configuration is only for dev purposes

Hope this thread will avoid future head aches
Thx again


Nicolas

---

### Post by TheFu on 2013-08-08
Glad to help.

BTW, I'd put your web server files somewhere else - not under HOME.  If you must, create a softlink from HOME to the real location.  Allowing a different userid to write under your HOME just feels really, really, really bad. Security alarms are going off in my head.  Still, it is your box - do what you like.

---

### Post by ndaval on 2013-08-09
Actually my sites are in a "web" dir (whose owner is www-data) in my home dir...

---

### Post by TheFu on 2013-08-09
> **ndaval said:**
> Actually my sites are in a "web" dir (whose owner is www-data) in my home dir...

Yes, I had assumed that, but it doesn't change the fact that the real files under your HOME are owned by a different user. THIS is bad.  Again, it would be better to have the actual files located in an area of disk where we expect different users to own files, then link to that from your HOME as you like ... or just use the **cdpath** environment variable.  These are security considerations and it is best to avoid bad habits from the start.

---

