---
title: "problems with unity and gnome classic desktops - how to reinstall and clean them"
date: 2013-04-04
forum: Desktop Environments
---

### Post by Jaoyur on 2013-04-04
I have ubuntu 12.04.02 and I always uses kde 4.10.1. Sometimes I need  to swith to unity or gnome classic (with effects), the problem is that  when I log in with one of them I can't access to "settings menu" or  other menus because they do not appear. I think I have messed up some  time ago but I don't remember. Maybe it is a problem concerned to  compiz.   I have tried to use ```
unity --reset
``` and ```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity 
```commands to reset gnome2 and unity but still the same thing.

  So is there a way to reinstall compiz or gnome classic and unity in order to clean them like when I have installed ubuntu first time? (I just would like to reinstall them without making any change to kde desktop.)

  Thanks

---

### Post by Kirboosy on 2013-04-04
You could run a 

```
sudo apt-get purge compiz*
``` Which will remove everything associated with compiz.

Then you can reinstall it using

```
sudo apt-get install compiz
```

That will reinstall it like you are looking for.

---

### Post by Jaoyur on 2013-04-05
thanks, I did that but same problem with gnome classic, some settings menu do not appear.

edit: I re-installed also gnome classic and unity (also common files) and now everything works fine thanks

---

