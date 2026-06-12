---
title: "Apache permissions and file access."
date: 2009-04-30
forum: General Help
---

### Post by nzkronic on 2009-04-30
Hi, 

I have recently done a fresh install of the the latest Ubuntu and did not backup my apache files.

I have reinstalled apache and now want to serve files from my Media Partition which is mounted on startup at /media/Media

Below I have listed what I have in my apache config file. How do I change the settings here or in a chmod command so I can access these files from a browser without the "403 Forbidden you do not have access to / on this server"

Thanks in advance. 


```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /media/Media
	<Directory />
		Options FollowSymLinks
		AllowOverride None
		allow from all
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
```

---

### Post by nzkronic on 2009-04-30
Have found the problem, needed the Indexes option

---

