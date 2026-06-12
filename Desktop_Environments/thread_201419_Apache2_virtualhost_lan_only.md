---
title: "Apache2 virtualhost lan only"
date: 2006-06-21
forum: Desktop Environments
---

### Post by darkstarshadow on 2006-06-21
Hey, I have been working the past couple days to get this working right, so far.... mostly working. What I am trying to do is host multiple sites, wich after alot of searching I got my virtualhosts to work. The thing is, I want to make one that has phpmyadmin and a few other things only visable to my lan, and keep the rest open to the internet. Every thing I have tried has had it just go to my first vh. Any ideas ? Oh, and sorry, I wasnt entierly sure where to post this. And yes I know, my spelling sucks.

Thanks in advance for the help.

---

### Post by jvl on 2006-06-21
mod_access ( [http://httpd.apache.org/docs/2.0/mod/mod_access.html](http://httpd.apache.org/docs/2.0/mod/mod_access.html) ) is your friend.

edit your httpd.conf:

<Directory /path/to/web/directory>
Order Allow, Deny
Allow from 192.168.0.0/24
Deny from all
</Directory>

This would enable access only from the LAN ip range, which is in this case 192.168.0.0/24

Hope this helps.

---

### Post by darkstarshadow on 2006-06-21
Ok, I can see that working for permisions and stuff, but how do I actually access it, I am useing a namebased virtualhost. And thank you for the quick respones

---

### Post by jvl on 2006-06-22
You need to set up appropriate DNS records for the world to see.

A record for the main virtualhost and CNAMEs for the other virtualhosts pointing to the A record. (Your domain administrator could help you with that) 

By design, SSL name based virualhosts won't work. (PTR points to the primary record always, so there will be certificate warnings)

---

