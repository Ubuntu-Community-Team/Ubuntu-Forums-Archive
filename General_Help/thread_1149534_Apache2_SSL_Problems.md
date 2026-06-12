---
title: "Apache2 SSL Problems"
date: 2009-05-05
forum: General Help
---

### Post by Manasia on 2009-05-05
Hello Ubuntu Clan,

I have been pulling my hair out, trying to setup ssl on my Ubuntu server. I finally got everything working (Or so I thought), no error messages from apache or anything but when I visit my server I get this error in Firefox:

[I]Data Transfer Interrupted

The connection to addison was interrupted while the page was loading.

The browser connected successfully, but the connection was interrupted while transferring information.  Please try again.

    * Are you unable to browse other sites? Check the computer's network connection.
    * Still having trouble? Consult your network administrator or Internet provider for assistance.[/I]

Here are the most recent lines in my access.log:

68.184.140.122 - - [04/May/2009:20:33:19 -0400] "\x16\x03\x01" 200 11645 "-" "-"
127.0.0.1 - - [04/May/2009:20:36:09 -0400] "GET /" 200 81 "-" "-"
127.0.0.1 - - [04/May/2009:20:41:05 -0400] "GET /" 200 81 "-" "-"
127.0.0.1 - - [04/May/2009:22:55:13 -0400] "GET /" 400 594 "-" "-"
127.0.0.1 - - [04/May/2009:23:03:04 -0400] "GET /" 400 594 "-" "-"

At first I was getting the x16, I fixed my cert and I am using the self-signing .pem cert. Here is my default-ssl file:

NameVirtualHost *:443
<virtualhost *:443>
       ServerAdmin webmaster@localhost
        SSLEngine On
        SSLCertificateFile /etc/ssl/private/localhost.pem

DocumentRoot /var/www/
       <directory />
               Options FollowSymLinks
               AllowOverride None
       </directory>

       <directory /var/www/>
               Options Indexes FollowSymLinks MultiViews
               AllowOverride None
               Order allow,deny
               allow from all
               # This directive allows us to have apache2's default start page
               # in /apache2-default/, but still have / go to the right place
               # Commented out for Ubuntu
               #RedirectMatch ^/$ /apache2-default/
       </directory>

<Directory /var/www/webdav/>
    Dav On

     Options Indexes FollowSymLinks
    AllowOverride None

     AuthType Basic
    AuthName "OpenVista document imaging"
    AuthUserFile "/etc/apache2/htpasswd"
    Require valid-user
</Directory>

       ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
       <directory "/usr/lib/cgi-bin">
               AllowOverride None
               Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
               Order allow,deny
               Allow from all
       </directory>

Any help would be appreciated. I did not realize setting up SSL would be so difficult.

---

