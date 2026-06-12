---
title: "PHP files won't execute"
date: 2006-03-11
forum: Desktop Environments
---

### Post by dan4444 on 2006-03-11
Don't know what changed, but everytime I try to open even the most basic of /var/www/*.php files in firefox, nothing happens at all, almost like it is not excecuting the script at all.

I even tried installing PHP 5 again, but apt-get told me PHP was already installed and updated to the most current version.

FYI: The test of testphp.php that I was instructed to run the first time installed PHP5 did actually run successfully, but won't any longer.

Anyone know what I need to tweak to get this working again?

---

### Post by ElijahLofgren on 2006-03-11
I've had problems setting up test servers on various distros and have started to use XAMPP instead of going to all the trouble of setting everything up. Try it, you might like it: [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by adamkane on 2006-03-11
Try using synaptic and mark the apache/php/mysql packages for "Complete Removal", then re-install. 

It's likely some small issue with one of the .conf files. Very hard to track down the setting that is causing the problem.

You can install ubuntu-lamp by adding the Sevea repository through source-o-matic.
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by dermotti on 2006-03-11
Did you add 

AddType appllication/x-httpd-php .php


to your httpd.conf?

---

