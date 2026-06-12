---
title: "How to open up public_html to the web?"
date: 2009-05-10
forum: General Help
---

### Post by jseiser on 2009-05-10
I have created 2 joomla websites on my desktop PC.  I access them by going to [http://localhost/joomla](http://localhost/joomla) and [http://localhost/otel/joomla](http://localhost/otel/joomla) .  They are saved in /home/user/public_html/joomla /home/user/public_html/otel/joomla respectively.  I want to show a few people these websites, so I know I need to open up the ports in my router and forward them to my PC.  I can do this for things like torrenting, but I am at a loss as to how to do this when it comes to my sites. I have read that I want to forward port 80 or 8080.  I would rather forward 8080 just to try and keep it off the normal port.  I can get in my router and change whatever is needed. Any one have any ideas how to do what I want?

tl/dr I need help making my two websites accessible over the internet.

edit: Thanks that worked.

---

### Post by gradysghost on 2009-05-10
I'm going to assume that you're running Apache 2.  By default, this is configured to use port 80.  If you want to change that to 8080, you need to edit the ports.conf file.  You'll find this in /etc/apache2

Look for these two lines:

```
NameVirtualHost *:80
Listen 80
```

And change them to

```
NameVirtualHost *:8080
Listen 8080
```

Restarting Apache should make this take effect.  To restart, execute this:

```
sudo /etc/init.d/apache2 restart
```

Make sure you set up the appropriate port forwarding on the router.  I wish I could give you specifics on this, but every router is different, and I'm afraid you'll have to refer to your user's guide.  You can usually find those online at the manufacturer's website.

After all of that config is done, you should be able to access your site using [http://localhost:8080](http://localhost:8080), and others should get it at [http://yo.ur.ip.addy:8080](http://yo.ur.ip.addy:8080)

You can also head over to [dyndns.com]("http://www.dyndns.com") and get a free DNS name to route to your system.  This service comes on high recommendation from me personally, since I use it and love it.

Hope this helps!

---

