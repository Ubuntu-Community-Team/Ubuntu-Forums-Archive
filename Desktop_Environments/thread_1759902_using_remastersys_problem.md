---
title: "using remastersys problem"
date: 2011-05-16
forum: Desktop Environments
---

### Post by wayne1980 on 2011-05-16
hi im usin ubuntu 10.4 and when i follow this page
[http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22/](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22/)

it seems to bring this problem up

wayne@wayne-desktop:~$ gksu gedit /etc/apt/sources.list
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/wayne@wayne-deskremastersys/ttp://www.geekconnection.org/remastersys/repository  
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
wayne@wayne-desktop:~$ deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
wayne@wayne-desktop:~$ deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/sudo apt-get update
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
wayne@wayne-desktop:~$ sudo apt-get install remastersys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remastersys
wayne@wayne-desktop:~$ 

any ideas how to fix this and thank u 4 all your time you take to check this out

---

