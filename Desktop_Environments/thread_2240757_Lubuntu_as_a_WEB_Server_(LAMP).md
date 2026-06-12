---
title: "Lubuntu as a WEB Server (LAMP)"
date: 2014-08-22
forum: Desktop Environments
---

### Post by graylinux on 2014-08-22
Hi

I am setting up my website on a Lubuntu Linux m/c using LAMP. The Lubuntu is an 14.04 LTS virtual machine (VM) running VMWare VMPlayer hosted on a Windows 7 PC. It is intend to be an Intranet server eventually.

My website requires a login. When running in the Linux VM and specifying localhost/formtools in my browser I can login and the site runs as it should. When I try to use my website from the Windows 7 host however all I get is the website login prompt (but curiously none of the graphics of the login page?). 
I can also see the 'index of' my linux web server from the Windows 7 host. 

When I enter my credentials into my website I can see the browser trying to fire up the req'd index.php but I get a 'cannot display webpage' (from I.E.) 

I don't think the host/vm setup is the problem because I also have phpmyadmin on my Linux VM which I can happily access from the Windows 7 host.

I am guessed this might be a permissions problem and I got so desperate I temporarily did a chmod -R 777 /var/www/html/mywebsite but this did not fix it.

Any ideas anyone?

---

### Post by graylinux on 2014-08-22
Hi

I have solved this.

My website installation has a config file...  config.php.  In it is a php variable $root_url_parameter...  curiously I had to change this from a 'full' URL of "http://localhost/mywebsite" to just "/mywebsite".

I can now access it from the Windows host.

HTH someone somewhere!

---

