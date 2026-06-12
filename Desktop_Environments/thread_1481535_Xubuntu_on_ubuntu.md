---
title: "Xubuntu on ubuntu"
date: 2010-05-12
forum: Desktop Environments
---

### Post by qwerty123321 on 2010-05-12
When I try to install xubuntu through 

```
sudo aptitude update && sudo aptitude install  xubuntu-desktop 
```I get the following error..What should I do??? I  want to be able to choose between gnome and xfce...

```
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Leave the following dependencies unresolved:
catfish recommends slocate
Score is -81

Accept this solution? [Y/n/q/?] ^C

```

---

### Post by azertyh on 2010-05-13
hi,
if you want to use just xfce or to have the choice between gnome and xfce at the session login, you can install it by :
```
sudo aptitude install xfce4
```

---

