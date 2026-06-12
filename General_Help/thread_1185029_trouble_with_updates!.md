---
title: "trouble with updates!"
date: 2009-06-11
forum: General Help
---

### Post by darwinpunch on 2009-06-11
hey everyone. i've been having problems trying to run updates on my computer and installing new apps on ubuntu... this error always pops up:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i don't know if i am trying to fix the problem in an intelligent manner, but i tried running the dpkg command in terminal, which promps the response that i need to be logged onto the administrative account on the computer (this is the only account on the computer! ). 

does anyone know what is wrong or how i could fix it? thank you so much!!!

---

### Post by DougieFresh4U on 2009-06-11
Open up terminal  Applications.Accesseries<Terminal and
```
sudo dpkg --configure -a
```

---

### Post by darwinpunch on 2009-06-11
ha, thank you so much. simplicity wins today...

---

### Post by DougieFresh4U on 2009-06-11
Your welcome :p When I do updates, (via terminal) I always do it this way:
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude -f install
sudo dpkg --configure -a
```
one at a time
Glad to have you among us!!

---

