---
title: "Good HTML Editot For Ubuntu"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-03
Hi all!!

I am making a website and right now I am using bluefish (Not such a great program) Does anybody here know of a better HTML Editor that is able to run on ubuntu?

Thanks

---

### Post by aysiu on 2006-09-03
"Better" in what sense? What do you feel Bluefish is lacking?

You might want to try Amaya, Screem, Nvu, or Gedit.

---

### Post by Ignacio Monge on 2006-09-03
Try with these one:
* [Quanta Plus]("http://quanta.kdewebdev.org/").
* [Nvu]("http://www.nvu.com/").
* [Kompozer]("http://kompozer.net/") (a Nvu fork).

---

### Post by Magiczero on 2006-09-03
Bluefish is missing all kinds of things and is hard for me to use.  I like dreamweaver for windows!  Great app!

---

### Post by foolsh on 2006-09-03
nvu is a wysiwyg editor i like it somewhat like dreamweever im not sure if it s in the universe multiverse package tree or in the default main restricted package repositories 
try 
```
sudo apt-get install nvu
```
if that does not work
```
sudo gedit /etc/apt/sources.list
```
and add
```
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse  
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse  
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 


```
save
then 
```
sudo apt-get update
sudo apt-get install nvu
```
after that i recommend reversing the changes to your sources.list file before you 
```
sudo apt-get upgrade
```

---

### Post by RobsterUK on 2006-09-03
I've also come from using Dreamweaver and today I've been trying out all the programs suggested in this thread among others.

My conclusions are that Nvu is the closest you'll get to Dreamweaver as it combines WYSIWYG with site management functions.

Although I would point out that it won't let you open anything other than HTML files. I think there are plugins to let you open PHP etc in a text editor but nothing built in. This is a problem for me as my main site is all PHP files that are mostly HTML with a few includes

---

