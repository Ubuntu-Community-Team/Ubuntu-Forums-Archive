---
title: "can i get the new unity on kubuntu 11.10?"
date: 2011-10-06
forum: Desktop Environments
---

### Post by Jack_Coleman on 2011-10-06
Im not talking about the beta, im saying when it comes out in 5 days, can i get kubuntu 11.10, go into terminal, and say "sudo apt-get install unity" and get basically a unity 2.0/kde 4.7 dual setup on the login screen kinda thing going? also ill probably want to get gnome 3 and maybe the classic 2 in there also if that matters, but i know how to do that.

also, could i do it vice versa? get ubuntu 11.10, and get KDE 4.7 on there? i just assumed it would be easier to get unity.

P.S. i much perfer KDE 4.7 (like seriously, its amazing) but i dont want to miss out on the ability to use the new unity. and i dont feel comfortable dual booting them because it seems unnecessary and im using chameleon with windows and hackintosh os x S.L. so i think three is enough.

---

### Post by wolfen69 on 2011-10-06
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Jack_Coleman on 2011-10-06
> **wolfen69 said:**
> ```
sudo apt-get install ubuntu-desktop
```
Thats it? and that gives me the new unity?

---

### Post by proxy.qtz on 2011-10-07
Yes it does. It also gives you basically all of the ubuntu-specific packages, so you'll have 2 different sets of applications that serve the same purpose.

---

### Post by Krytarik on 2011-10-07
If I were you, and I really only want to have the Unity interface, and want to keep running only the already installed apps through it, I'd first try installing only the package "gnome-session":

[http://packages.ubuntu.com/oneiric/gnome-session](http://packages.ubuntu.com/oneiric/gnome-session)

And don't worry, "suggests" aren't installed by default; otherwise, it would pull in the whole Gnome DE through those. :P

Regards.

---

