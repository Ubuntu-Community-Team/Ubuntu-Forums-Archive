---
title: "screenlets"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by xoron on 2007-10-04
hi

i am pretty new to ubuntu

i was wondering as to how i can install screenlets

i have been to the gnome-look.org site and downloaded some...but i dont know what to do with them...they are .tar.gz files if it helps

sombody told me to to add some hendrik.kaju repositry bt i get this error
--------------------------------------------------------------------------------

ubuntu:~$ wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update
Password:--09:38:14--  [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg)
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
09:38:14 ERROR 404: Not Found.

--------------------------------------------------------------------------------

ask if you need more information

---

### Post by dj Kalma on 2007-10-04
Have you checked out the [instructions on that site]("http://hendrik.kaju.pri.ee/ubuntu/")? 

Based on the site, you have at least the .gpg file's address wrong, it should be [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg)

---

### Post by Chymera on 2007-10-04
You have to install the screenlets program itself, you can either get it from the repository that was mentioned above, or from the official site [http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)

Then, if you want to have better control over their behavior, set their window type to "widgets" (through the right click menu), and activate the compiz fusion screenlets plugin.

---

