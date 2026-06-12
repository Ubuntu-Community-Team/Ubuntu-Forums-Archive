---
title: "couldn't find package CCSM..."
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by comjo on 2007-08-26
root@comjosbaby:/etc/apt# sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package compizconfig-settings-manager**
root@comjosbaby:/etc/apt# sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
root@comjosbaby:/etc/apt# sudo apt-get install ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **Couldn't find package ccsm**
root@comjosbaby:/etc/apt# 


What repository can I add to get apt-get insall ccsm to work?

I'm a n00b. (to linux)

Brandon

---

### Post by Vorian on 2007-08-26
what repositories are you using now?

(and you shouldn't run as root)

---

### Post by ddrichardson on 2007-08-26
> **Vorian said:**
> what repositories are you using now?

(and you shouldn't run as root)

Especially when you're sudo'ing as well ;-)

---

