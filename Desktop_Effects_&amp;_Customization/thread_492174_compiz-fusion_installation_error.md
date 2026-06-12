---
title: "compiz-fusion installation error"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by malanco on 2007-07-04
hi, im new here, im very new to linux, im using ubuntu Feisty Fawn, and i wanted to install compiz-fusion, everything went fine till i get this error : 

agustin@ubuntu:~$ sudo apt-get -y upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
agustin@ubuntu:~$ sudo apt-get -y install compiz compiz-gtk compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gtk: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but 1:0.5.1+git20070703~3v1ubuntu0 is to be installed
E: Broken packages


what i am doing wrong?? :(

---

