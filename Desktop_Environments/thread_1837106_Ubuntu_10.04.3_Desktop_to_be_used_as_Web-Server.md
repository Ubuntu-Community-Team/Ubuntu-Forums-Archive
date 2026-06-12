---
title: "Ubuntu 10.04.3 Desktop to be used as Web-Server"
date: 2011-09-01
forum: Desktop Environments
---

### Post by Vasudev102 on 2011-09-01
Hi, I've loaded Ubuntu 10.04.3 (Lucid) Desktop version in my laptop and I wish to use it as a Webserver.  Can someone guide me the steps involved to achieve success in this activity.
 
Thanking you in anticipation,
 
Vasudev102

---

### Post by sanderj on 2011-09-01
A webserver for what / whom? Accessible from your LAN, or from Internet?

---

### Post by edgreenberg on 2011-09-01
Here is a totally basic answer to get you started. 

Using Synaptic Package Manager, install the apache2 package, and everything that wants to come with it.   Then start apache using the command line:   sudo /etc/init.d/apache2 start

Poof, you have a web server. Put your content in /var/www

You will doubtless have more questions, so ask away.

---

