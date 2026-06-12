---
title: "Apache Not working Please Help"
date: 2009-04-18
forum: General Help
---

### Post by joec369 on 2009-04-18
Hello I'm trying to setup Apache Web Server. What I have done:

Installed Apache
Turned it on
Made a config file
Made a directory where the website is /home/(username)/public_html
Made a simple webpage
I also downloaded Firestarter, and put in an exception in the firewall for http port 80, everyone.

It works if I'm on the Ubuntu Machine. I type in [http://localhost/](http://localhost/) in FF and it comes up with my simple html site I made.

But if I try to access the website from another computer on my LAN it doesn't work. I'm typing in [http://10.0.2.15/](http://10.0.2.15/) (10.0.2.15 is the IP address of Ubuntu Machine) in FF.

Both machines can ping each other. Also should mention that both machines are Virtual box guests. Both in the Same network/subnet.

[B]This is the config file I've been working with:
[/B]
<VirtualHost *:80>
ServerAdmin webmaster@localhost

DocumentRoot /home/joe369/public_html
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /home/joe369/public_html>
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

**Any help would be greatly appreciated!!!!**

---

### Post by _Purple_ on 2009-04-18
Did you try [http://10.0.2.15:80](http://10.0.2.15:80) ?

---

### Post by joec369 on 2009-04-18
Yes I tried a bunch:

[http://10.0.2.15](http://10.0.2.15)
[http://10.0.2.15:80](http://10.0.2.15:80)
[http://10.0.2.15/](http://10.0.2.15/)
[http://10.0.2.15:80/](http://10.0.2.15:80/)
10.0.2.15:80
10.0.2.15

None of them worked.

I was looking in the log file specified in the configuration.  And this error keeps showing up:

[Sat Apr 18 01:03:59 2009] [error] [clien 120.0.0.1] File does not exist; /home/joe369/public_html/favicon.ico[B]

Is that Important?[/B]

---

### Post by _Purple_ on 2009-04-18
I think if you give details about your LAN setup and router, it will help us to figure out your problem.

---

### Post by joec369 on 2009-04-18
I have one actual computer running WinXPpro.  I have virtual box installed, two Virtual machines.  XP and Ubuntu.  The Xp and Ubuntu machines are on their own network, using the NAT option in Virtual Box.  XP = 10.0.2.2/24 Ubuntu = 10.0.2.15/24.  They both can ping each other.

The 'host' computer is on a different subnet 192.168.1.100/24.  The XP 'host' is connected to the internet through a WRTG Linksys router.  And the virtual machines can also access the internet if needed.

---

### Post by joec369 on 2009-04-18
Well I guess no new ideas.  I guess I'll just have to try and install Ubuntu on an actual computer and see if apache works then.

---

