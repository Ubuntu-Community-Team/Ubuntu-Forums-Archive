---
title: "Apache user in Ubuntu 8.04"
date: 2009-05-28
forum: General Help
---

### Post by aniketto on 2009-05-28
Hi all,
 
I am new to ubuntu and Linux also :D
 
I have installed ubuntu 8.04 LTS. I have also installed and configured Apache2, PHP and mysQL.
 
Now I wanted to deploy my PHP application. This application was previously deployed on Cent OS. CentOS used 'Apache' and not 'Apache2' . 
Also when you install 'Apache' in CentOS it creates a user Apache. But when we installed Apache2 on Ubuntu, it didnt create any user like 'Apache2'.
Coming to point, my application's deploy.sh does some 'chown' work with Apache user in CentOS. What can I do to have it work in Ubuntu?
 
Is there any option while installing Ubuntu to create the Apache2 user.
 
Thanks in Advance,
Aniketto

---

### Post by upbeat.linux on 2009-05-28
You should probably check out both the Ubuntu wiki and documentation for Apache 2.  

**_[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")_**

**_[http://httpd.apache.org/docs/2.0/]("http://httpd.apache.org/docs/2.0/")_**

Unless you compiled from source user and group default to www-data.

---

