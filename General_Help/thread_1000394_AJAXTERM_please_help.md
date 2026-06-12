---
title: "AJAXTERM please help"
date: 2008-12-02
forum: General Help
---

### Post by mrjerryk on 2008-12-02
I have Ajaxterm installed and it's working fine.  Can someone please tell me how to make it so the window will scroll the text.  Right now if I do a ps -e or any other command, the output scrolls of the screen.  I have seen other sites do this but won't share their secrets other than they are using Ajaxterm.

Any help is appreciated.

Thanks.

---

### Post by mrjerryk on 2008-12-07
bump

---

### Post by mewbie on 2009-06-16
mrjerryk :popcorn:

**Please** if you could take a look at my post here:
[http://ubuntuforums.org/showthread.php?p=7418105#post7418105](http://ubuntuforums.org/showthread.php?p=7418105#post7418105) to see if you can help me get AjaxTerm to work properly as I read that yours is working.
Maybe you could post the apache2 file you changed for this?

Thank you for time and appreciate the help!

---

### Post by mrjerryk on 2009-06-16
I followed this guide step by step and mine works great.  [https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm)

I also used these tutorials to setup apache.

[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5)

[http://articles.slicehost.com/2007/9/27/ubuntu-feisty-apache-ssl-and-vhosts](http://articles.slicehost.com/2007/9/27/ubuntu-feisty-apache-ssl-and-vhosts)

You follow everything above then it should work.  That's all I did.

---

### Post by mewbie on 2009-06-20
**mrjerryk thank you for your reply** :D
That is the tutorial that I followed as well. 
My apache2 is working fine without the AjaxTerm added to its config.
I'm thinking where I might have gone wrong is the part that says:
> You will now need to go access the vhost settings which [here at least..] are located in sites-enabled 
sudo nano -w /etc/apache2/sites-enabled/**000-default**
Remove the line; NameVirtualHost * and edit the first Vhost to include the port 80; <VirtualHost *> change to <VirtualHost *:80>. 
Add an entry for the new port number and proxy to the AjaxTerm  etc etc

When I added those settings to the file '000-default' apache2 wouldn't start because, if I recall correctly,  it had two different ports on its file (80 & 443) and complained about that. I even tried various ways of adding these settings to that file. 

So I ended up adding this section to: /etc/apache2/sites-enabled/**ssl**
Apache2 would start, just entire site (no matter what URL) was directed to the AjaxTerm Page. Further more the login on AjaxTerm terminal wouldn't work.. the window was basically useless. Also the AjaxTerm page itself [http://myurl.com:8022](http://myurl.com:8022)
wouldnt' work at all and nor would https work on entire site any longer. 

So if you would be a doll and pastebin.com your entire /etc/apache2/sites-enabled/**000-default** file **or whatever/any file** you added the AjaxTerm entry to, that I'm sure would be a *huge* help to my puzzle. :D

Thank you very much again! ):P


  *

---

### Post by mewbie on 2009-06-23
I thought I should clarify something. On the tutorial ([https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm)) it says to >  
Remove the line; NameVirtualHost * and edit the first Vhost to include the port 80; <VirtualHost *> change to <VirtualHost *:80>. 
Add an entry for the new port number and proxy to the AjaxTerm1. Neither file has this line: **NameVirtualHost *** to remove
2. **<VirtualHost *:80>** This was already on the file 000-default.

*Note on AjaxTerm README.txt it says to have these two lines at the top of configurations (I tried also; site won't work):
    Listen 443
    NameVirtualHost *:443

I tried adding the configs the tutorial gives to the bottom of my 000-default file and get error:
Reloading web server config: apache2[Tue Jun 23 12:17:14 2009] [warn] _default_ VirtualHost overlap on port 443, the first has precedence

I've tried blending them in and site won't start.

I then try adding them to my /etc/apache2/sites-enabled/ssl
again site won't start or various errors depending how I add them. Please if you could post your entire file/s that you have edited for AjaxTerm. This is my ssl file with all ajaxterm entries commented out (or site won't work):

<VirtualHost *:443>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem
#        SetEnvIf Request_URI "^/u" dontlog
#        ErrorLog /var/log/apache2/error.log
#        Loglevel warn
#
#        ProxyRequests Off
#        <Proxy *>
#                AuthUserFile /srv/ajaxterm/.htpasswd
#                AuthName EnterPassword
#                AuthType Basic
#                require valid-user
#
#                Order Deny,allow
#                Allow from all
#        </Proxy>
#        ProxyPass / [http://localhost:8022/](http://localhost:8022/)
#        ProxyPassReverse / [http://localhost:8022/](http://localhost:8022/)

        <Directory />
                Options None
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride AuthConfig
                Order allow,deny
                allow from all
                AuthUserFile /etc/apache2/.htpasswd
                AuthGroupFile /dev/null
                AuthName  "Authorization Required"
                AuthType Basic
                require user mynamepass
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
        Options -Indexes MultiViews FollowSymLinks               
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>         

--end

Thank you again from a very frustrated and bummed out mewbie :(

---

