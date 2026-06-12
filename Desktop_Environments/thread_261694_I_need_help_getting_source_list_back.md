---
title: "I need help getting source list back"
date: 2006-09-20
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-20
trying to upgrade from dapper to edgy (I'm using a machine just laying around). I was following forum members how to to and after changing dapper's to edgy's I crash sort of. Lost all my source list and can not get it to come up and synaptic is empty Also can I upgrade using the edgy cd I burned?

---

### Post by LotsOfPhil on 2006-09-20
[http://ubuntuguide.org/wiki/Dapper#Repositories]("http://ubuntuguide.org/wiki/Dapper#Repositories")

---

### Post by DougieFresh4U on 2006-09-20
dougie@dougiestoybox:~$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_b ackup
Password:
dougie@dougiestoybox:~$ deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main rest ricted universe multiverse
bash: deb: command not found
dougie@dougiestoybox:~$ ## Add comments (##) in front of any line to remove it f rom being checked.
dougie@dougiestoybox:~$ ## Use the following sources.list at your own risk.
dougie@dougiestoybox:~$
dougie@dougiestoybox:~$ deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restric ted universe multiverse
bash: deb: command not found
dougie@dougiestoybox:~$ deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main res tricted universe multiverse
bash: deb-src: command not found
dougie@dougiestoybox:~$
dougie@dougiestoybox:~$ ## MAJOR BUG FIX UPDATES produced after the final releas e
dougie@dougiestoybox:~$ deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main  restricted universe multiverse
bash: deb: command not found
dougie@dougiestoybox:~$ deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
bash: deb-src: command not found
dougie@dougiestoybox:~$
dougie@dougiestoybox:~$ ## UBUNTU SECURITY UPDATES
dougie@dougiestoybox:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security ma in restricted universe multiverse
bash: deb: command not found
dougie@dougiestoybox:~$ deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-securit y main restricted universe multiverse
bash: deb-src: command not found
dougie@dougiestoybox:~$
dougie@dougiestoybox:~$ ## BACKPORTS REPOSITORY (Unsupported.  May contain illeg al packages.  Use at own risk.)
dougie@dougiestoybox:~$ deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports ma in restricted universe multiverse
bash: deb: command not found
dougie@dougiestoybox:~$ deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backport s main restricted universe multiverse
bash: deb-src: command not found
dougie@dougiestoybox:~$
dougie@dougiestoybox:~$ ## PLF REPOSITORY (Unsupported.  May contain illegal pac kages.  Use at own risk.)
dougie@dougiestoybox:~$ deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non- free
bash: deb: command not found
dougie@dougiestoybox:~$ deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
bash: deb-src: command not found
dougie@dougiestoybox:~$  
dougie@dougiestoybox:~$ ## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
dougie@dougiestoybox:~$ ## servers. RealPlayer10, Opera and more to come.)
dougie@dougiestoybox:~$ deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by LotsOfPhil on 2006-09-20
Ummm.... all that is supposed to go in the file /etc/apt/sources.lst

You missed the line:
gksudo gedit /etc/apt/sources.list

---

