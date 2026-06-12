---
title: "Web Server setup question"
date: 2009-06-18
forum: General Help
---

### Post by mykrob on 2009-06-18
Hey-

I want to do LAMP on my laptop for mobile testing of sites I work on without having to upload.

What packages do I need to install in Synaptic/Aptitude, and also how do I define locations? For example, I want to place sites I am working on in /home/user/Documents/Website

What file do I need to edit to make certain directories active so it works form the browser locally?

Thanks,
-myk

---

### Post by t4thfavor on 2009-06-18
There is an option on the Ubuntu server cd to install a LAMP stack. Also you could Google "+ubuntu +LAMP" and you will find a load of howtos. Its really not hard, but somebody should really put together a metapackage (or whatever) called LAMP that installs exactly that.

---

### Post by credobyte on 2009-06-18
Open your terminal and execute this command :
```
sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mysql mysql-server

```
It'll install Apache, PHP and MySQL. If you need a way to modify MySQL databases/users in GUI mode, install *mysql-admin* or *phpmyadmin*.

---

### Post by t4thfavor on 2009-06-18
Next time I will get you a spoon :) +1 to above as that is the exact command I would have used if I could have remembered it off hand.

---

### Post by Celauran on 2009-06-18
For the location question, you could specify /home/you/Documents/Website as the server root. What I prefer doing, though, is to set up virtual hosts so I can work on multiple sites at once (ie. /home/me/www/sitea, /home/me/www/siteb, and so on).

You'll also need to edit your /etc/hosts file if you want to access your test sites by URL other than [http://localhost/whatever](http://localhost/whatever).

```
127.0.0.1 localhost a.example.com b.example.com
```
and so on.

---

### Post by Tibuda on 2009-06-18
or you can delete /var/www and create a link to your folder.
> mkdir ~/Website
cd /var
sudo rm -fr /var/www
sudo ln -sf ~/Website www

---

### Post by mykrob on 2009-06-28
How do you change the webserver root? I need to know the name of the file to edit

---

### Post by mcduck on 2009-06-28
> **mykrob said:**
> How do you change the webserver root? I need to know the name of the file to edit

/etc/apache2/sites_available/

You can either edit the default site configuration, or add a new one and then use a2ensite-command to enable your new site.

---

### Post by mykrob on 2009-06-28
> **Celauran said:**
> For the location question, you could specify /home/you/Documents/Website as the server root. What I prefer doing, though, is to set up virtual hosts so I can work on multiple sites at once (ie. /home/me/www/sitea, /home/me/www/siteb, and so on).

You'll also need to edit your /etc/hosts file if you want to access your test sites by URL other than [http://localhost/whatever](http://localhost/whatever).

```
127.0.0.1 localhost a.example.com b.example.com
```
and so on.

I'd like more information on setting up Virtual hosts in the way discussed above. Please advise,

Thanks,
-myk

---

