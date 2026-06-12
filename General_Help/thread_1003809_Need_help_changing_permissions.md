---
title: "Need help changing permissions"
date: 2008-12-06
forum: General Help
---

### Post by clay7 on 2008-12-06
Hello,

I installed 8.10 about 12 hours ago, and I'm the only user on this box. Synaptic installed PHP, Apache2, phpMyAdmin, and MySql 5 for me.

THe member 'unutbu' helped me out with permissions by pointing me to a page that told me I need to so something like this:

sudo chown bob:bob /home/bob/*

But I need to change permissions for entire directories higher than this because I'm trying to configure Apache2 and phpMyAdmin files, but they all say I don't have permission. These are in directories like: 

/var/www/
/etc/phpmyadmin/
/usr/share/phpmyadmin/

SO...How do I change permission for all of these? I think I would follow the example above but since i'm a complete newb, I just want to verify. Would I need to do anything else?

---

### Post by phidia on 2008-12-06
You don't want to change permissions on system files for security and safety reasons.
See the Ubuntu wiki on file servers [here]("https://help.ubuntu.com/community/Servers"). Look for the section titled "Web Servers".

---

### Post by clay7 on 2008-12-06
but i need to change permissions on the apache config file so I can run phpMyAdmin. Otherwise, it won't work.

---

### Post by phidia on 2008-12-06
> **clay7 said:**
> but i need to change permissions on the apache config file so I can run phpMyAdmin. Otherwise, it won't work.

How are you trying to run the configuration?

I'm not an expert in web servers. You really should look at this page [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").  

If you need administrative privilege you need to either open the application from the terminal with "gksudo" or if you can do the configuration in command line simply use "sudo".

---

