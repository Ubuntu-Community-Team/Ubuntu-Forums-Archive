---
title: "Change locales with simple way"
date: 2006-06-07
forum: Desktop Environments
---

### Post by linuxmangr on 2006-06-07
Hi to All becouse a setup Dapper Drake I find to need change locales.
I use this locales :
el_GR.ISO-8859-7
el_GR.UTF-8
en_US.ISO-8859-1
en_US.UTF-8
ru_RU.ISO-8859-5
ru_RU.UTF-8
But I try to find how I can change it and can't to find only I find this way 
open console and go to cd /var/lib/locales/supported.d/
I find some files for me I find el,en,local,ru I ediut by hand to files and insert locale what need to use and this is simple way but if you need some other locales to use for first thing you need to install lang support for this locale and after edit this files .
Ubuntu is the Best Linux Distro! I very like it!I use it in my work and home!
P.S. sorry for my english.

---

### Post by NiN on 2006-06-07
There are a number of ways:

gui based go to system/preferences?/locale chooser and set your default language

at the login screen you can choose your language before you log in

in the cli you can do a dpkg-reconfigure locales

hope that helps

P.S. you still have to install the language support to get translated strings ;)

---

