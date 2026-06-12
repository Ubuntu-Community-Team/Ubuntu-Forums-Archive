---
title: "Wordpress install on Ubuntu"
date: 2009-05-15
forum: General Help
---

### Post by optique on 2009-05-15
I am interested in installing wordpress locally (not remotely), before I spring for web hosting. In other words, I want the ability to create users, author wordpress pages, post. 

I am interested in hearing from anyone who has installed, and used wordpress, especially concerning the level of difficulty to get it to work as described above. 

I have moderate experience with ubuntu.

Thanks
steve.

---

### Post by FluffyElmo on 2009-05-15
Haven't installed Wordpress but have run many LAMP programs locally. It's a pretty easy process generally. This looks like it may be what you're looking for?[http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp](http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp)

The same blog has instructions on installing LAMp (first step), you can jump to the installing apache part and go from there.
[http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu](http://www.supriyadisw.net/2006/12/lamp-installation-on-ubuntu)

Good Luck!

---

### Post by Kareeser on 2009-05-15
Because Wordpress is a dynamic web application suite, you will need a LAMP stack, as **FluffyElmo** has mentioned.

You will need to install Apache, MySQL, and PHP. If you don't know how to interface with MySQL directly, you will need a third party package like phpMyAdmin.

You will also need to know how to edit permissions and ownerships across directories with the chown and chmod commands.

The install is fairly simple, since it is all handled by scripts run by the web install. Just download, untar, and navigate to the index.html page.

---

### Post by optique on 2009-05-16
> **Kareeser said:**
> Because Wordpress is a dynamic web application suite, you will need a LAMP stack, as **FluffyElmo** has mentioned.

You will need to install Apache, MySQL, and PHP. If you don't know how to interface with MySQL directly, you will need a third party package like phpMyAdmin.

You will also need to know how to edit permissions and ownerships across directories with the chown and chmod commands.

The install is fairly simple, since it is all handled by scripts run by the web install. Just download, untar, and navigate to the index.html page.

On the web hosting sites, they advertise wordpress as a 5min install. They make it appear like you avoid having to know much about Mysql, Apache and PHP. 

Are you saying that on Ubuntu, a fair knowledge of these three items IS required? Sorry, just confused as to the level of expertise required to get Wordpress running on Ubuntu.

thanks.
Steve.

---

### Post by elianthony on 2009-05-16
Hi Steve,

You don't need a knowledge of any of the three requirements for performing this install. I've successfully installed Wordpress locally on 3 different machines running 8.04 by following this tutorial... [http://www.jonathanmoeller.com/screed/?p=235]("http://www.jonathanmoeller.com/screed/?p=235")

I don't know which version of ubuntu you're running, but I hope this helps.

---

### Post by optique on 2009-05-16
> **elianthony said:**
> Hi Steve,

You don't need a knowledge of any of the three requirements for performing this install. I've successfully installed Wordpress locally on 3 different machines running 8.04 by following this tutorial... [http://www.jonathanmoeller.com/screed/?p=235]("http://www.jonathanmoeller.com/screed/?p=235")

I don't know which version of ubuntu you're running, but I hope this helps.

I read the linked info and it did seem within my skill set. I will try and thanks for the info.
Steve.

---

### Post by javaholic5 on 2009-09-27
There's a good guide on that here:
[http://www.ludisoft.com/knowledgebase/?p=3](http://www.ludisoft.com/knowledgebase/?p=3)

It caters more to (k)ubuntu though.

---

