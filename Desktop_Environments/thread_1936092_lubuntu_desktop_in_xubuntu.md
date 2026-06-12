---
title: "lubuntu desktop in xubuntu"
date: 2012-03-05
forum: Desktop Environments
---

### Post by MeriMeri on 2012-03-05
can i install Lubuntu desktop on Xubuntu (10.04)??
only its desktop, not any additional software.

thank you all

---

### Post by 2F4U on 2012-03-05
In 11.10 the package would be called lubuntu-core or lxde, but I am not sure if such a package exists for 10.04.

---

### Post by snowpine on 2012-03-05
Lubuntu uses the LXDE desktop. Compare these lists:

[http://packages.ubuntu.com/lucid/lxde](http://packages.ubuntu.com/lucid/lxde)
[http://packages.ubuntu.com/lucid/lubuntu-desktop](http://packages.ubuntu.com/lucid/lubuntu-desktop)

Install **lubuntu-desktop** for the full Lubuntu experience, or **lxde** for just the LXDE desktop (no extra applications).

---

### Post by TheFu on 2012-03-05
I don't know the exact answer, but if you drop to a terminal and type:

$ sudo apt-get update
$ sudo apt-get install lxde

then all the dependencies will be displayed.  If you don't like them all, answer "no" and walk away.

---

