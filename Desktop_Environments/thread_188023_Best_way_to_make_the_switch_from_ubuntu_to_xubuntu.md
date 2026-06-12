---
title: "Best way to make the switch from ubuntu to xubuntu"
date: 2006-06-03
forum: Desktop Environments
---

### Post by pspotts on 2006-06-03
Folks,

On June 1, I upgraded Ubuntu from 5.10 to 6.06 (along with the rest of humanity) and after the upgrade, I noticed xubuntu. Having played with XFCE back when I was using another, ahem, distro, I was impressed with its speed and leanness. I'd like to know if there's a way -- short of a clean install -- to replace ubuntu 6.06 with xubuntu 6.06. True confessions: I posted this on the email list for ubuntu users. One person gave me the distro-upgrade command set for xubuntu but said it would reside side by side with ubuntu. I'm looking to have only xubuntu on the hard drive. I'm not interested in being able to switch back and forth between the ub flavor and the xub flavor...but I'd also like to avoid a from-scratch install if at all possible. How hopeless a quest is this?

Best,

Pete

---

### Post by tobiaspb on 2006-06-03
Hi.

Just install xubuntu-desktop via synaptic and you will have xubuntu. Log out and in. If you would like to remove the gnome desktop then remove the ubuntu-desktop and it's dependencies, but gdm is used by xubuntu to.

Hope it helped.


- Tobias B.

---

### Post by aysiu on 2006-06-03
[QUOTE=tobiaspb]Hi.

Just install xubuntu-desktop via synaptic and you will have xubuntu. Log out and in. [/quote] I wouldn't use Synaptic, but that is the basic procedure. For more details: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu) > If you would like to remove the gnome desktop then remove the ubuntu-desktop and it's dependencies Not such an easy task if you favor Synaptic or apt-get over aptitude. ```
sudo apt-get remove ubuntu-desktop
``` does essentially nothing. You'd have to use *deborphan* or *gtkorphan* to remove *ubuntu-desktop*'s dependencies.

---

