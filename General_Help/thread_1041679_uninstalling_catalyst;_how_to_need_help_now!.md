---
title: "uninstalling catalyst; how to? need help now!"
date: 2009-01-16
forum: General Help
---

### Post by Thowsen on 2009-01-16
Hi, ive recently installed ubuntu again which Im happy of doin. but i got a little problem, well, its big for me lol :D.
I screwed up my catalyst installation and now catalyst wont boot. so i think the best way is just to uninstall and reinstall again.
but how do i uninstall catalyst?
Im really really a newbie at this so please be kind, Im learnin new things everyday :)

so the question is:
how do i uninstall Ati Catalyst 8.12?

---

### Post by Thowsen on 2009-01-16
sry for bumpin' but i really need help, Im off to a game event tomorrow and i would really appreciate to have my computer with me :)

---

### Post by Yellow Pasque on 2009-01-16
If it's the Ubuntu repo version:
```
sudo apt-get purge xorg-driver-fglrx
```
If it's a version you got from the ATI website, run /usr/share/ati/fglrx-uninstall.sh, something like:
```
cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh
```

---

### Post by Thowsen on 2009-01-17
thanks , you're the man :D

---

