---
title: "ServerName? info?"
date: 2009-03-19
forum: General Help
---

### Post by Spikerok on 2009-03-19
I was tring to find some info on error

"apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName"

i know how to fixit, in wiki it states
create new file
"sudo nano /etc/apache2/conf.d/fqdn"
Add line
ServerName localhost


the think is, that "ServerName localhost" makes me think that my web server will be only available on the local mashine, that why i was thinking of changing it on my ip address.. and i just wanted to know more info about it, after looking on apache wiki i got even more confused, if it fits what my problem or not because

"Syntax:	ServerName [scheme://]fully-qualified-domain-name[:port]"
why use localhost without port?

so please could some one explain that part clearly, many thanks.


[link about error]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[info on apache about servername]("http://httpd.apache.org/docs/2.2/mod/core.html#servername")

---

### Post by fieroboom on 2009-03-19
I'm really glad you're asking instead of just following that command, because that isn't the proper way to fix it. Apache2 warning you of not finding a fully qualified domain name (FQDN) means that it is looking for one of these two scenarios:
- Your computer's hostname to be 'somedomain.com'
or...
- You site configuration to have a ServerName directive with a FQDN

...and it isn't finding either of those. I personally don't ever change my hostname, because I'm always running virtual servers, so it's many 'servers' on one IP address. All you need to do is edit your site's configuration file (/etc/apache2/sites-available/default or 000-default), and add a ServerName directive.
Here is an example from the config file for one of my sites, alabamafieros.com:
```
<VirtualHost *:80>
        ServerAdmin paul@grandesigns.net
        ServerName alabamafieros.com
        DocumentRoot /var/www/alabamafieros
        CustomLog /var/log/apache2/alabamafieros.log common
        <Directory />
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch FollowSymLinks
                AllowOverride None
        </Directory>
#       <Directory /var/www/alabama/newpics>
#               Options Indexes
#       </Directory>
</VirtualHost>
```

In my BIND9 config, I have a wildcard pointed to alabamafieros, so that anything.alabamafieros.com gets handled by Apache, which allows me to do custom subdomains quickly, and each of those has it's own ServerName directive:
```
<VirtualHost *:80>
        ServerAdmin paul@grandesigns.net
        ServerName forum.alabamafieros.com
        DocumentRoot /var/www/alabamafieros/forum
        <Directory />
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch FollowSymLinks
                AllowOverride None
        </Directory>
</VirtualHost>
```

Does that make sense? If not, let me know, and I'll explain it further.
:D
-Paul

---

