---
title: "Apache not following symlinks to home/USER on separate partition"
date: 2009-05-19
forum: General Help
---

### Post by happyhobbit on 2009-05-19
Hi,

I have a separate partition mounted under /home 

fstab entry - 

```
# Mount /dev/sda6 120gb partition as /home ext4
UUID=f1d81a48-3bfd-4218-b7e7-b50bcec16234 /home ext4 noatime 0 2
```

I'm trying to create a website development set up, and I want my htdocs (and mysql files - yet to figure that one out) on my home partition.

For some reason I can't get apache to follow symlinks to my home partition.

My 'default' file in /etc/apache2/sites-available is same as when first installed - 

```
DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
```


and when I moved the www folder to a another folder on the same partition as / (I used /media) and put a link called www in /var pointing to /media/www and reloaded apache, I still got 'It works'.

But if I put a link in /var called www pointing to /home/me/webdev and reload apache I get a 500 internal server error...

Possibly this is a permissions issue but I temporarily changed /home/me to 777 and still no joy

Any ideas greatly appreciated I have been trying to figure this out for a while now :confused: ... !

---

### Post by happyhobbit on 2009-05-19
FIXED - found an erroneous .htaccess file in my /home/me/webdev I must have copied at some point from a drupal install. Discovered it after looking in /var/log/apache2 and saw the line 

[Tue May 19 12:51:11 2009] [alert] [client ::1] /var/www/.htaccess: Invalid command 'Header', perhaps misspelled or defined by a module not included in the server configuration

doh!

---

