---
title: "Setup Webserver on Ubuntu PC?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by erusan on 2006-09-01
How can I setup Ubuntu, using perhaps a service such as no-up.com, to run as a personal web server?  My free provider doesn't use php, and the server is quite unstable (stupid Apple).

---

### Post by Uluen on 2006-09-01
Depends, will you use it as desktop as well?
If you grab the server-iso, there is an option to install a "LAMP"-server that might be what you need.

---

### Post by erusan on 2006-09-01
Yes, I'll be using it as a desktop as well.  I'd like to just run it over the install I have right now, since it's less than a week old.

I tried installing the apache2 package, then using no-ip.com to redirect, but it's not working.

---

### Post by Uluen on 2006-09-02
Are you forwarding port 80 to this computer? How do you update no-ip.com, with ddclient?

If it's set up correctly, a "ping yourhostname.no-ip.com" should return your external IP, the same as [http://whatismyip.com/](http://whatismyip.com/) gives.

---

### Post by Matt Yun on 2006-09-02
See [LAMP Installation on Ubuntu 6.06 for Noobs]("http://howtoforge.org/lamp_installation_ubuntu6.06"), on the excellent howtoforge.org site.  LAMP stands for "Linux Apache MySQL PHP" (although the P can also stand for Perl or Python).

---

### Post by BENSTER on 2006-09-02
In the past I've installed apache to my Desktop Ubuntu and my user account for web page was /home/benster/public-html/index.html

haven't tried out this latest version though, and I'm setting up a LAMP this time.

**EDIT**  Looks like it's not gonna be so easy with Server LAMP install.  :)  I'm tempted to use Webmin now.  :)

---

### Post by greeklegend on 2006-09-03
The default location of your website is /var/www but you can change it sonewhere in httpd.conf i think.
There shouldn't be any need for the server iso, all you need to do is install the packages you want through synaptic and use port forwarding on your router to open up your webserver. What kind of router do you have?

---

### Post by BENSTER on 2006-09-03
I went in to /etc/apache2/apache2.conf  but it's a little large for me right now.  :)  Having cgi-bin and public-html really makes things simple for me, although I have use /var/html/ in the past.  I will have 3 virtual domains set up on this box.

I noticed ports.conf was called, so I chagned that from 80 to 8787.  I use an ASANTE router with port 8787 for http to escape notice from the cable company.   My intention though is to make this box my router/firewall as well as my web server.  I have 2 NIC's installed, I just haven't read any guides on setting it up yet.

I installed Webmin .deb but it is setup for apache - not apache2 and as a result it can't find the configs.  I'd be smarter in the end to do things the hard way....it'll make me learn just a little bit more, but virtualmin makes it easy to add domains.

---

