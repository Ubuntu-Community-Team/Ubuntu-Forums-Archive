---
title: "XAMPP localhost not connectiing"
date: 2009-02-06
forum: General Help
---

### Post by retrodans on 2009-02-06
I am running ubuntu 8, and have installed xampp.  I went into the vhosts file and ammended it to read:

[HTML]#
# Virtual Hosts
#
# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.2/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /home/retrobadger/working_files/retrobadger.net
	ServerName local.retrobadger.net

	<Directory "/home/retrobadger/working_files/retrobadger.net">
		Options Indexes FollowSymLinks Includes ExecCGI
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>
</VirtualHost>[/HTML]

I then went into the hosts file and added the correct line to go to local.retrobadger.net.  And finally went into the httpd.conf file and uncommented the line:
[HTML]Include etc/extra/httpd-vhosts.conf[/HTML]

But when I go to the url local.retrobadger.net it redirects me to local.retrobadger.net/xampp and tells me that:
[HTML]The requested URL /xampp/ was not found on this server.[/HTML]

---

### Post by retrodans on 2009-02-08
*bump*

---

### Post by retrodans on 2009-02-10
For anyone looking into this too, I have solved the issue I was having, and it was all rather silly.  Doin g a ctrl+refresh wasn't enough to refresh firefox, you have to clear the whole of the browser cache, then it should work properly.

Hope this helps someone.

---

