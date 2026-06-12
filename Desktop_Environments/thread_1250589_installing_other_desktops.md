---
title: "installing other desktops"
date: 2009-08-26
forum: Desktop Environments
---

### Post by linuxhippy on 2009-08-26
I'm running xubuntu 9.04.  How do I install other desktops with apt-get?

---

### Post by NoaHall on 2009-08-26
"sudo apt-get install kubuntu-desktop"
"sudo apt-get install gnome-desktop"

---

### Post by fela on 2009-08-26
sudo apt-get install kde
sudo apt-get install xfce

I know kde works like that, not too sure about xfce.

Note this will only install the base files, if you want all the apps aswell go for kubuntu-desktop and xubuntu-desktop, respectively. There's also edubuntu-desktop and ubuntustudio-desktop which includes LOADS of apps.

---

### Post by Grifulkin on 2009-08-26
And [here](http://www.psychocats.net/ubuntu//puregnome) is a link to get back to Pure GNome if you don't like the others, and there are links to get pure KDE and Xfce as well incase you like one more instead.

---

### Post by tuxxy on 2009-08-26
> **NoaHall said:**
> "sudo apt-get install kubuntu-desktop"
"sudo apt-get install gnome-desktop"

I think the second one should have been;

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Dullstar on 2009-08-26
Don't use ubuntu/kubuntu/xubuntu desktop!
That's my warning.  Use

sudo apt-get install [desired DE here]

Exmaples:

sudo apt-get install gnome
sudo apt-get install kde
sudo apt-get install xfce
sudo apt-get install lxde

---

