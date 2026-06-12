---
title: "Apache + PHP5"
date: 2005-12-16
forum: General Help
---

### Post by so0le on 2005-12-16
Hello, so I got probelms with Apache + PHP5, I did these commands at terminal:

sudo apt-get install apache2
sudo apt-get install php5

And removed # in front of UserDir and the other directory thing from apache2's .conf file.

So the apache works fine, I can for example watch .png files trough my server, but .php s wont work. They give the following error messages:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/home/joel/public_html/moi.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Anyone help? And please, explain clearly, im new at Linuxes/Ubuntu, so I may not understand any advanced things, thanks!

---

### Post by ape on 2005-12-16
make sure that you have the libapache2-mod-php5 package installed also.

---

### Post by so0le on 2005-12-16
Yes, I have it. It says its the newest version, so does apt-get install php5 say too. This is weird problem. :/

---

### Post by FizDev on 2006-01-06
*bump* I have the same problem =S

---

### Post by FizDev on 2006-01-06
I've reinstalled everything following this :
[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28Apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28Apache%29)
Now everything works wonderfully, I simply have php4 instead of php5 =)
I suppose it was because I had wrongly configured php5

---

