---
title: "gnome-do issue need help"
date: 2008-06-05
forum: Desktop Environments
---

### Post by angelus_kit on 2008-06-05
Dear all 

i need a help, i installed ubuntu server 8.04 and after i installed the gnome-do 
commande line 
apt-get update 
apt-get install gnome-do

after that when i type #gnome-do -q or gnome-do or gnome-do -quiet i have a message error 

[B](Do:4556):Gtk-WARNING **: cannot open display 
[/B]
please anybody can help

---

### Post by kellemes on 2008-06-06
> **angelus_kit said:**
> Dear all 

i need a help, i installed ubuntu server 8.04 and after i installed the gnome-do 
commande line 
apt-get update 
apt-get install gnome-do

after that when i type #gnome-do -q or gnome-do or gnome-do -quiet i have a message error 

[B](Do:4556):Gtk-WARNING **: cannot open display 
[/B]
please anybody can help

The server edition of Ubuntu doesn't include X, that's no graphical user interface.. gnome-do needs it.
If this is what you want you need to install it (probably) like so..
```
sudo apt-get install ubuntu-desktop
```
May take some time ;-)

---

### Post by angelus_kit on 2008-06-15
Dear 

thanks you for your help it's worki now 

Best regard

---

