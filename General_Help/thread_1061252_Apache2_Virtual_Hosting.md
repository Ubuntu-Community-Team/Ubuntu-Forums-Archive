---
title: "Apache2 Virtual Hosting"
date: 2009-02-05
forum: General Help
---

### Post by sjl127 on 2009-02-05
Forgive me if this already here, but I've looked and am posting this as a last resort...

Is there any clear-cut documentation about configuring apache2 on intrepid for virtual hosting?  

I'm familiar with this on windows, with simple editing to the system 32 hosts file and httpd.conf.

But, it seems more complicated and more involved with linux and I can't find just one source about how do to this that's in an easy manner...

Thank you...

---

### Post by jtoth on 2009-02-05
I was just having this same problem... they changed a few things from version 1 to version 2 as well :3

Check out \etc\apache2\conf.d the individual configurations for your virtual sites should be in there.  I discovered this on accident, so I can't quite point you to any documentation.

---

### Post by sjl127 on 2009-02-05
It's very simple and not complicated at all.

Name based virtual hosts, multiple websites for one IP.

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

The only file I manipulated was apache2.conf and all I did was add these lines to the very end:
```

NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.domain.tld
ServerAlias domain.tld *.domain.tld
DocumentRoot /www/domain
</VirtualHost>

<VirtualHost *:80>
ServerName www.otherdomain.tld
DocumentRoot /www/otherdomain
</VirtualHost>
```

---

### Post by spiderbatdad on 2009-02-05
The above should be done in the file /etc/apache2/sites-available/your_site

You create the file by making a copy of the /sites-available/default file file, and edit for your vhosts. Then disable the default site and enable your_site ```
sudo a2dissite default && sudo a2ensite your_site
```Generally avoid editing /apache2.conf, instead put your configuration changes in httpd.conf. This file will take presidence over apache2.conf where configuration changes are made.

---

### Post by sjl127 on 2009-02-05
My burning question is this:  Now what if I revert my apache2.conf back to what it was...  

What would the file look like in that folder?  

What exactly do I have to create and what exactly do I have to do?

---

### Post by spiderbatdad on 2009-02-05
```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/my_site
``` Now edit the new file for your virtual hosts```
sudo nano /etc/apache2/sites-available/my_site
```ctrl+o then enter to save. ctrl+x to exit. Enable the site as explained above.
Restart apache: ```
 sudo /etc/init.d/apache2 restart 
```

---

### Post by spiderbatdad on 2009-02-05
I have a tutorial here: [http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)
It isn't the greatest but it should give you the basics...including authentication at the end.

---

