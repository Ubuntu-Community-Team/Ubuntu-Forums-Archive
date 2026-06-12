---
title: "Mythtv localhost and phpmyadmin"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Jmerlos on 2006-08-30
I am following this guide for installing mythtv under ubuntu, [http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html) and after entering **localhost** in firefox apache opens but when i click on the hyperlink for phpmyadmin it wants to save instead of allowing you to loggin as root. Any help is appreciated.

---

### Post by tytus on 2006-10-25
Try 127.0.0.1 or ip address of your box instead of localhost. This works for me (I have the same problem when I try localhost).

---

### Post by superm1 on 2006-10-30
If you are installing on a more modern system then breezy, follow a more modern installation guide...

Did you ever resolve this?

---

### Post by Denamite on 2006-11-01
I got this exact same problem, Firefox wants to save the myphpadmin link when i click it instead of opening it.
If anybody has any idea or suggestion I'll gladly listen.

---

### Post by superm1 on 2006-11-01
This typically happens when php isn't properly installed on the machine.  If you have no other important web stuff being hosted on apache, the easiest way to solve it is to remove and purge the config for all apache*, & *php*.

In other words, open up synaptic, and search for apache.  Right click anything that is related to the apache server, libapache*, modules, etc.  and hit remove and remove configuration.  Do the same thing for php.

Once this is done, install phpmyadmin (but nothing else).  It will resolve the dependencies correctly and install/configure apache and php for you.

---

### Post by Denamite on 2006-11-01
Seems like phpmyadmin doesn't want to install apache, mysql-server, it just prompts for:
libmysqlclient15off
mysql-common
php5-cgi
php5-common
php5-mysql
php5-mysqli

for whatever reason.

---

### Post by superm1 on 2006-11-01
Oh you seem to be right about this.  I believe I got apache server because I did mythweb followed by phpmyadmin.  


I'll have to double check this in a VM later on today.  If you don't get it later on, I'll try to post back with results.

---

### Post by clark3rd on 2006-11-01
> **superm1 said:**
> This typically happens when php isn't properly installed on the machine.  If you have no other important web stuff being hosted on apache, the easiest way to solve it is to remove and purge the config for all apache*, & *php*.

In other words, open up synaptic, and search for apache.  Right click anything that is related to the apache server, libapache*, modules, etc.  and hit remove and remove configuration.  Do the same thing for php.

Once this is done, install phpmyadmin (but nothing else).  It will resolve the dependencies correctly and install/configure apache and php for you.

Okay, I did this, and it still wants to save the file. what else can I do?

---

### Post by superm1 on 2006-11-01
Okay guys,

I went through in a virtual machine myself to check this out.   You need libapache2-mod-php5 installed in order for it to work.  If you still get this trying to download the phtml file, then clear your Firefox cache and try once more.

---

### Post by clark3rd on 2006-11-02
> **superm1 said:**
> Okay guys,

I went through in a virtual machine myself to check this out.   You need libapache2-mod-php5 installed in order for it to work.  If you still get this trying to download the phtml file, then clear your Firefox cache and try once more.

That was it. Thanks!

---

