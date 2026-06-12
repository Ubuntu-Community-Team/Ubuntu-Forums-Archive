---
title: "Installing Xfce on Gusty"
date: 2007-10-30
forum: Desktop Environments
---

### Post by -Stevey-Wonder-1990- on 2007-10-30
quick question,

How do i install the xfce desktop environment on Gusty 7.10?

---

### Post by santiagoward2000 on 2007-10-30
quick answer, :)
```
sudo apt-get install xubuntu-desktop
```

---

### Post by aysiu on 2007-10-30
> **santiagoward2000 said:**
> quick answer, :)
```
sudo apt-get install xubuntu-desktop
```
Either you can paste that command in [the terminal](http://www.psychocats.net/ubuntu/terminal) or you can go to System > Administration > Synaptic Package Manager, mark *xubuntu-desktop* for installation, and then *Apply* changes.

I would recommend pasting *this* command in instead. It makes removing Xfce easier later, should you wish to do so: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` More details here: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by santiagoward2000 on 2007-10-30
> **aysiu said:**
> Either you can paste that command in [the terminal](http://www.psychocats.net/ubuntu/terminal) or you can go to System > Administration > Synaptic Package Manager, mark *xubuntu-desktop* for installation, and then *Apply* changes.

I would recommend pasting *this* command in instead. It makes removing Xfce easier later, should you wish to do so: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` More details here: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

Hey aysiu!
Perhaps this is off-topic, but could you explain what the difference is? Thanks!

---

### Post by aysiu on 2007-10-30
> **santiagoward2000 said:**
> Hey aysiu!
Perhaps this is off-topic, but could you explain what the difference is? Thanks!
*aptitude* will remember what dependencies came along with the newly installed package. *apt-get* will in most cases, but I haven't seen it reliably do so for large metapackages like *ubuntu-desktop* or *kubuntu-desktop.*

---

### Post by carlos1992 on 2007-10-30
really apologize for this question (it's stupid) but why is good (or why people do it) install other enviroments *e. xfce, kde, etc* in a linux with other enviroment or you uninstall the other enviroment and leave the one you like

---

### Post by santiagoward2000 on 2007-10-30
> **aysiu said:**
> *aptitude* will remember what dependencies came along with the newly installed package. *apt-get* will in most cases, but I haven't seen it reliably do so for large metapackages like *ubuntu-desktop* or *kubuntu-desktop.*

Ahhh! OK! Thanks!!

---

