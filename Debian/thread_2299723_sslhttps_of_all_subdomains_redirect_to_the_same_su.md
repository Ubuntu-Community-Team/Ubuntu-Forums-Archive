---
title: "ssl/https of all subdomains redirect to the same subdomain &amp; .htaccess redirect"
date: 2015-10-20
forum: Debian
---

### Post by asteriks on 2015-10-20
I have strange problem and don't know where to look for error.

I installed debian jessie/8 and I have 2 domains with several subdomains.
http is working normal, all domains and subdomains, except still I didn't succeed to make working rewrite rules in .htaccess files, for example subdomain mijaw.bla.com should redirect to mijaw.bla.com/en/index.html
in my case, it is redirected to en folder but not to en/index.html

I disabled all but you can see how it looked, I tried and without inde.html, just EN, but no success:
```

#<IfModule mod_rewrite.c>
#RewriteEngine On
#RewriteCond %{HTTP_HOST} ^bla\.com$
#RewriteRule (.*) http://mijaw.bla.com/$1 [R=301,L]
#RewriteRule . /en/index.html/$1 [L,QSA]
#</IfModule>

```

```
root@vmi50113:/var/www/html/hosting# a2enmod rewrite
Module rewrite already enabled
```

but my main question is about ssl, where to find error in next problem:
http**s**://mijaw.bla.com and all other subdomains like [https://john.bla.com](https://john.bla.com) or [https://travolta.bla.com](https://travolta.bla.com) bring me to the same subdomain: [https://mijaw.bla.com](https://mijaw.bla.com) 
I can make 100 subdomains but all of them in https bring me to the same subdomain.

so, it can be virtualhost in apache, it can be mod_ssl, 
I disabled default-ssl.conf in /etc/apache2/sites-available
all ssl sites are enabled... I don't have any idea where to look for error and solution. 

here is an example of ssl virtualhost file:
```
<IfModule mod_ssl.c>
        <VirtualHost *:443>
                ServerAdmin webmaster@localhost
                ServerName john.bla.com
                DocumentRoot /var/www/html/john
                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined

SSLEngine on
SSLCipherSuite ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA
SSLHonorCipherOrder on

                SSLCertificateFile /etc/ssl/certs/apache.crt
                SSLCertificateKeyFile /etc/ssl/private/apache.key

                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>

                BrowserMatch "MSIE [2-6]" \
                                nokeepalive ssl-unclean-shutdown \
                                downgrade-1.0 force-response-1.0
                # MSIE 7 and newer should be able to use keepalive
                BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

 </VirtualHost>
</IfModule>

```

I tried to comment #SSLCipherSuite but it didn't help, I kept it from older installation of iredmail but this is now reinstalled server, iredmail is deleted, just I copied backed up virtualhost file. ssl is working, but it brings all subdomain to the same subdomain. if I type [https://bla.com](https://bla.com) again it will bring me to [https://mijaw.bla.com](https://mijaw.bla.com)

---

### Post by asteriks on 2015-10-21
I changed this part and it is working now, I added IP and :443 in servername:
<IfModule mod_ssl.c>
        <VirtualHost 1.2.3.4:443>
                ServerAdmin webmaster@localhost
                ServerName john.bla.com:443

redirect is still problem. 
in both cases I have subfolders:
/var/www/html/subdomain/english/index.html
present situation [http://subdomain.bla.com](http://subdomain.bla.com) brings me to subdomain and then I must click english folder to get index.html
I can't get .htaccess file to bring me to english folder and not to subdomain folder.

---

### Post by asteriks on 2015-10-22
one subdomain problem is solved but it is not functional for another one where I have /en/index.html, /se/index.html and one more language.
my working solution was to include next line in virtualhost john.conf (/etc/apache2/sites-available): DirectoryIndex /languageFolder/index.html
it worked even I have 2 languages, I can click another language and I get it, but it is not working in other subdomain with 3 languages, I get always english and css and other files are not accessible (by apache possible), it shows text without design. strange.

---

### Post by asteriks on 2015-10-23
one subdomain is working with next code in .htaccess:
> <IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule ^$ /language/$1 [L,QSA]

another one with 3 languages subfolders is working with next code, I just removed /:
> <IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule ^$ /en$1 [L,QSA]
</IfModule>

---

