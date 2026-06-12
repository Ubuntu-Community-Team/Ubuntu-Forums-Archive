---
title: "screwed some things up"
date: 2009-01-21
forum: General Help
---

### Post by ocajublinky on 2009-01-21
okay so, trying to find out what heck certain things are, I may have screwed things up, I have missing links in menu and on top of that my adress bar is really effed up

my manager (synaptic), when I try to reinstall the broken symbolic links, gives me this error:
E: /var/cache/apt/archives/gnome-applets-data_2.24.1-0ubuntu1_all.deb: subprocess new pre-removal script returned error exit status 127
E: /var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_amd64.deb: subprocess new post-removal script returned error exit status 127

I think that  this is the root of my problem, I have tried reinstalling but I still get that error

---

### Post by ocajublinky on 2009-01-21
Im missing alot of programs

---

### Post by oldos2er on 2009-01-22
Try these commands entered one at a time in a terminal:

 ```
sudo apt-get clean

 sudo apt-get update

 sudo apt-get safe-upgrade
```

---

### Post by ocajublinky on 2009-01-22
says that the safe-upgrade is an E: invalid operation

---

