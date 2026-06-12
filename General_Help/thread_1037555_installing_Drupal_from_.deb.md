---
title: "installing Drupal from .deb"
date: 2009-01-11
forum: General Help
---

### Post by DouglasAWh on 2009-01-11
So, I've installed the Drupal package from [http://packages.debian.org/sid/all/drupal6/download](http://packages.debian.org/sid/all/drupal6/download)

Apache is running.  I get the "It works!" when I go to localhost.  How do I use that installed .deb to get Drupal going?  I don't think it matters, but I'm using Linux Mint.

Thanks!

---

### Post by DouglasAWh on 2009-01-11
ok, I found [http://drupal.org/getting-started/6/install/run-script](http://drupal.org/getting-started/6/install/run-script) but I don't know how or if the .deb set up Apache.  I do so little web stuff, Apache always frustrates me.

---

### Post by DouglasAWh on 2009-01-11
ok, I've discovered the files are in /etc/drupal/6.  In that dir I have files apache.conf and htaccess then subdir profiles and sites.  I think I'm going to call it a night.  I hope to have some useful into when I awake!

Thanks!

---

### Post by DouglasAWh on 2009-01-12
Ok, I think I've got the stuff in the correct directory using the instructions at [http://drupal.org/getting-started/6/install/download](http://drupal.org/getting-started/6/install/download) but I don't believe PHP is turned on. Any help with that?

---

### Post by Turd Ferguson on 2009-01-12
Synaptic has Drupal 5 maybe 6 isn't quite stable yet.

---

### Post by DouglasAWh on 2009-01-12
> **Turd Ferguson said:**
> Synaptic has Drupal 5 maybe 6 isn't quite stable yet.

Drupal is on 6.8.  It's been stable for a long time.  The .deb on the Debian site is 6.6.2.  I have a hard to believing no one on this site can help me turning on PHP in Apache.  I would have thought it was a simple thing.

---

### Post by aadityabhatia on 2009-07-31
> **DouglasAWh said:**
> ok, I found [http://drupal.org/getting-started/6/install/run-script](http://drupal.org/getting-started/6/install/run-script) but I don't know how or if the .deb set up Apache.  I do so little web stuff, Apache always frustrates me.
The apt installer added the drupal config file to "/etc/apache/conf.d" instead of "/etc/apache2/conf.d".

Moreover, based on the Ubuntu's way of dealing with the Apache config files, Drupal's config file should go to "/etc/apache2/sites-available/" directly, and the user should be provided the command to enable the site, which would look like "a2ensite drupal".

---

