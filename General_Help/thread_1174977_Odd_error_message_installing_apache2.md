---
title: "Odd error message installing apache2"
date: 2009-05-31
forum: General Help
---

### Post by litlfrog on 2009-05-31
When I try to install apache2, I get this:

> The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/45.8kB of archives.
After this operation, 102kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 
dpkg: serious warning: files list file for package `apache2-mpm-prefork' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apache2-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apache2.2-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapache2-mod-php5' missing, assuming package has no files currently installed.
179296 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.11-2ubuntu2_all.deb) ...
Setting up apache2 (2.2.11-2ubuntu2) ...


Given those "serious warnings," do I have to do something different here?

---

### Post by ActiveFrost on 2009-05-31
```
sudo apt-get install apache2
```
.. equals to what you tried to do ?

---

### Post by litlfrog on 2009-05-31
Yes, correct. Just tried sudo apt-get install apache2

---

### Post by litlfrog on 2009-06-04
OK, by reinstalling some apache2-utils, mpm-prefork, and the php mod, I got a clean install of apache2 with no errors. When I ran apache2 restart however, I got the following: 

> 
globalnet@xubuntu1:~$ sudo /etc/init.d/apache2 restart
[sudo] password for globalnet: 
 * Restarting web server apache2                                                Syntax error on line 143 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]


Line 143 is part of the following code block:
> <Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

Can anyone see what the problem is here? Thanks.

---

### Post by litlfrog on 2009-06-04
I've got it! Apparently when the program installed, there were no sites available--not even the default! I navigated to /etc/apache2/sites-enabled and ran

sudo ln -s /etc/apache2/sites-available/default

Once I restarted apache2, the page FINALLY loaded. :)

---

