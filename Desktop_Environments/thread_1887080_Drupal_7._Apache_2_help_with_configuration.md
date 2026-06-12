---
title: "Drupal 7. Apache 2 help with configuration"
date: 2011-11-26
forum: Desktop Environments
---

### Post by lucacerone on 2011-11-26
Dear all,
after my computer crashed I moved my drupal site to a different one
with a fresh Ubuntu 11.10 instalaltion.
I copied all the files and imported the mysql database.
The site was in maintenance mode when I made the backup,
and I'd like to login by accessing localhost/user
The page appears and I can insert my username and password
but after I click on the login button
it seems like the browser is loading something but then the user page is reloaded..
So I can't access my drupal site any more.

I think the issue might be with some  Apache configurations but I'm not an expert and I don't know what to change.
From a standard apache2 installation in Ubuntu
I only changed two things:
I've added AddType application/x-httpd-php .php to the /etc/apace2/apache2.conf file
and I've modified AllowOverride from none to All in the
<Directory /var/www/> block of the /etc/apache2/sites-enabled/000-default file.
(and restarted apache after of course)

Can somebody please help me understanding what is wrong and make the website work again on my computer? (this website is the backup of a site that is hosted and that works just fine on the host
provider, I just want a "development" version on my computer so that I can try modules and settings before
uploading it on the host).

Before my old computer broke I had Ubuntu 11.10 installed as well,
and I remember I modified a bit the configuration of Apache but I
just followed the suggestions I've found on some forum, and I don't
really remember what I changed.

Thanks a lot in advance to all you guys,
any help would be greatly appreciated!

P.s. I also asked this question on [http://drupal.org/node/1353248](http://drupal.org/node/1353248)
(I don't know the netiquette about cross-posting in here, I just thought
you might want to know ;))

---

### Post by lucacerone on 2011-12-01
Apparently I didn't have the PhP GD module installed.
Installing that solved the problem

---

