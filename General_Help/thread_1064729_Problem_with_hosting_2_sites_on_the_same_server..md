---
title: "Problem with hosting 2 sites on the same server."
date: 2009-02-09
forum: General Help
---

### Post by NewToApache2 on 2009-02-09
Hi,

I’m hosting 2 sites on the same Apache2 web server with python in the background. 
One is the default site and the other is the testing site for the default one. 
For the default site, the psp files are in /xxx/web and the python files are in /xxx/ pythonsource/scripts. For the testing site, the psp files are in /xxx/webtest and the python files are in /xxx/ pythonsource/scriptstest.

PythonPath is a global variable. So the psp files in the default site(/xxx/web) refers to the python files in the test location(/xxx/ pythonsource/scriptstest) if the test site is also launched. Is there a way to point the psp files in /xxx/web to the python files are in /xxx/ pythonsource/scripts ?

These are the config files for 2 sites.
For the default one
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /xxx/web/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>

	<Directory /xxx/web/ >
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order deny,allow
		allow from all

		PythonPath "sys.path+['/xxx/ pythonsource/scripts ']"
		AddHandler mod_python .psp
		PythonHandler mod_python.psp
		PythonDebug On

		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/

		DirectoryIndex index.php index.psp index.html
	</Directory>

	………………………………………………………………….

</VirtualHost>


For the testing site

NameVirtualHost *:8080
<VirtualHost *:8080>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /xxx/webtest/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>

	<Directory /xxx/ webtest/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order deny,allow
		allow from all

		PythonPath "sys.path+['/xxx/pythonsource/scriptstest`]"
		AddHandler mod_python .psp
		PythonHandler mod_python.psp
		PythonDebug On

		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/

		DirectoryIndex index.php index.psp index.html
	</Directory>

	………………………………………………………………………………………………………………………………………..

</VirtualHost>

---

### Post by hwttdz on 2009-02-09
I'm not sure I understand the question entirely, but you could try a symbolic link.

---

