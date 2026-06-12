---
title: "Firefox help"
date: 2006-08-16
forum: Desktop Environments
---

### Post by notoriouslou1022 on 2006-08-16
I'm trying to install firefox from the site. when i get the file which is a tar.gz and exact it then open termial and change to the directory, then i do ./configure and i get "no suck file or directory. So then i try in make and get "***no targets specified and no makefile found. stop.***" Also i did do sudo apt-get build-essials before i did all this... Please help, thanks

---

### Post by pdub on 2006-08-16
I will assume you are running Ubuntu 6.06. 

Firefox is already install in Ubuntu 6.06 so there is no need to install it. You can get the latest verion via apt. The latest is 1.5.0.5.

---

### Post by shoagun on 2006-08-16
You do not have to configure or make anything.  The tarball you get from the FF website has a bash script which runs firefox.  If you want firefox to be usable by all users, you should unpack it to a shared location.  I used 
/usr/lib , which is where ubuntu's version of firefox is.

do the following:

sudo mv /usr/lib/firefox /usr/lib/firefox_backup
sudo cp -r /<full path to unpacked FF directory>/firefox /usr/lib
sudo rm /usr/bin/firefox
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox


Alternatively, you can just leave the FF directory you unpacked wherever it is and just make the symbolic link.

---

### Post by notoriouslou1022 on 2006-08-16
i uninstalled it, i want to know why it is doin this tho...

---

### Post by shoagun on 2006-08-16
I don't think I understand what you're asking.  If you want to use the firefox available at the mozilla website, all you have to do is unpack the tarball and then go into the directory and type ./firefox

The method I outlined above allows you to replace the Ubuntu install of firefox if you had it installed.  If you want to use Ubuntu's firefox, just go to synaptec and install firefox.

---

### Post by notoriouslou1022 on 2006-08-17
sorry i was talking about the guy that posted before you, your stuff worked. THANK YOU SO MUCH MR.  :D

---

