---
title: "how to rewrite module in apache"
date: 2009-06-06
forum: General Help
---

### Post by tosunbd on 2009-06-06
Hello, I am a new user of ubuntu and also linux. Anyone can tell me how can enable apache 2 rewrite module.

Thanks..

---

### Post by ChrisDerson on 2009-06-10
Open a terminal window and type:

> sudo a2enmod rewrite
sudo apache2ctl graceful

This will ensure that the rewrite module is enabled, and restart the apache server to ensure the module is active.

---

### Post by tosunbd on 2009-07-03
Hello, this is not working.
when I run the first line the terminal shows the following message.

```


ERROR: Module rewrite not properly enabled: /etc/apache2/mods-enabled/rewrite.load is a real file, not touching i


```

please help me.

---

### Post by urko99 on 2010-09-10
Have the same problem.. Anything new by now? :)

---

### Post by phpmonkey on 2011-09-10
Sorry to drag up an old thread, but somebody may stumble across it as I did looking for the answer to this question.

I found the answer in this thread : [http://www.lavluda.com/2007/07/15/how-to-enable-mod_rewrite-in-apache22-debian/](http://www.lavluda.com/2007/07/15/how-to-enable-mod_rewrite-in-apache22-debian/)

I found that I got the error message @tosunbd mentioned when I had installed the module the "old way" (as described at the post I linked to) and then ran ```
sudo a2enmod rewrite
```
 as described.

You can check whether /etc/apache2/mods-enabled/rewrite.load alreday exists:
```
gedit /etc/apache2/mods-enabled/rewrite.load
```
It will probably contain the line
> LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so

If so, the module should be enabled anyway. If you want, you can change to the new way of enabling modules.

To do so, 

Delete the rewrite.load file
```
rm /etc/apache2/mods-enabled/rewrite.load
```

Re-install the module
```
sudo a2enmod rewrite

```


Now if you try running
```
sudo a2enmod rewrite

```
again, you will get the following message (instead of an error message):
> Module rewrite already enabled



You then:

Run
```
sudo gedit /etc/apache2/sites-available/default

```

Find the following
> <Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

and change it to

> <Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride **all**
		Order allow,deny
		allow from all
	</Directory>

And finally restart apache
```
sudo /etc/init.d/apache2 restart
```

Don't forget to enable the rewrite engine on the webpages in the .htaccess file
> RewriteEngine On

Apache's documentation is pretty darn good: [http://httpd.apache.org/docs/2.2/rewrite/](http://httpd.apache.org/docs/2.2/rewrite/)

---

### Post by pedrofuture on 2011-10-10
to @phpmonkey

I had module enabled and cant solve problem. but changing 'AllowOverride None' to 'AllowOverride all' in file /etc/apache2/sites-available/default solve it.


thank you very much :)

---

