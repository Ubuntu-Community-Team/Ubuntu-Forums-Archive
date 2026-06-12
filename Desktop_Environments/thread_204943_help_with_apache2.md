---
title: "help with apache2"
date: 2006-06-27
forum: Desktop Environments
---

### Post by tefflox on 2006-06-27
I have been reading this thread: [http://help.ubuntu-it.org/6.06/ubuntu/serverguide/it/httpd.html]("http://help.ubuntu-it.org/6.06/ubuntu/serverguide/it/httpd.html")

and I have enabled the server for 127.0.0.1 (acutally: my desktop name i.e, user@**[COLOR=DarkRed]computer, Listen computer:80 )[/COLOR]** but I can't get it to read my index.html file in my new Document root /home/username/apache

Here is my default file: 
NameVirtualHost *
<VirtualHost *>
        ServerAdmin my@email

        DocumentRoot "/home/myusername/apache/"

        <Directory "/home/myusername/apache/">
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

and when I restart apache2 I get this message: 

 * Forcing reload of apache 2.0 web server... apache2: 
Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName                  [ok]

What is going on? How do I get it to read my document root index file?  any help really appreciated

update: should I create some sort of link from this directory to my new document root:  **[COLOR=DarkRed]/var/www/apache2-default -> /home/... ?[/COLOR]**

---

### Post by tefflox on 2006-06-27
Now I have a strange problem.  I've been tooling with symlinks for the /var/www/ directory.. I can view localhost/apache2-default/ but not localhost/

How do I fix that?

---

