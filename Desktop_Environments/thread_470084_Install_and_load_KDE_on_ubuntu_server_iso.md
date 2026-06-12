---
title: "Install and load KDE on ubuntu server iso"
date: 2007-06-10
forum: Desktop Environments
---

### Post by cripperz on 2007-06-10
Hi guys,

previously i install ubuntu server feisty and somewhow, i would like to try running KDE like kubuntu on it. It is possible to install KDE and run it on boot without having to reinstall everything to Kubuntu desktop iso. Need some guidance or tips.

Thanx!!

---

### Post by taurus on 2007-06-10
Just install KDE with

```
sudo aptitude update
sudo aptitude install kubuntu-desktop kdm
sudo /etc/init.d/kdm start
```

---

### Post by cripperz on 2007-06-10
thanx for the quick reply. will try it out :)

---

