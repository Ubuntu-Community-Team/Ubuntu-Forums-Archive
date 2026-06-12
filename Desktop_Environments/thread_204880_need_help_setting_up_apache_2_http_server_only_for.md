---
title: "need help setting up apache 2 http server only for localhost"
date: 2006-06-27
forum: Desktop Environments
---

### Post by tefflox on 2006-06-27
I just used synaptic to install apach 2 mpm prefork for php 5, and I can find it with which or whatis.  I only want to run it on localhost so I can get my web pages right before sending them to my internet hosting service.  How do I configure it?

---

### Post by chickan on 2006-06-27
if you go into /etc/apache/ there will be several files there, like httpd.conf.dkpg-inst.queue.  All of those files, IIRC, need to be moved/renamed to just the .conf, in the same directory I believe.

edit httpd.conf, where it says "Listen:" to 
Listen <port>
Listen <ip>
ie: 
Listen 300
Listen 12.34.56.78:300

Also, you'll likely want to change the ServerRoot variable, as it defaults to /etc/apache.

---

### Post by tefflox on 2006-06-27
hello, and thanks.  will you look at my latest post in the general help?  I'm further along in the setup, have the server up and running, listening on localhost, but it wont read my document root. thanks

---

