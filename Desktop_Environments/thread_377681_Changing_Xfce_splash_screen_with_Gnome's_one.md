---
title: "Changing Xfce splash screen with Gnome's one"
date: 2007-03-06
forum: Desktop Environments
---

### Post by bravemosquito on 2007-03-06
After I changed Xfce with Gnome desktop, current splash screen is the same. Any ideas how to change it? Maybe this little problem shows a bigger and more serious trouble... :confused:

---

### Post by teaker1s on 2007-03-06
if it's in respositories then synaptic and search usplash

---

### Post by bravemosquito on 2007-03-06
Other ideas? When I tried to remove the splash there's a notification about "To be removed **ubuntu-desktop**" :mrgreen:

---

### Post by teaker1s on 2007-03-06
ubuntu-desktop is a meta package-with synaptic does it threaten to remove anything else?

---

### Post by bravemosquito on 2007-03-06
No, but a week ago when I removed it on another mashine (from Kubuntu to Ubuntu-desktop) all dependencies was destroyed... :-?

---

### Post by teaker1s on 2007-03-07
have you tried to 
```
sudo apt-get install xubuntu-artwork-usplash
```

what does it say?

---

### Post by bravemosquito on 2007-03-07
See the shot... :-s

Edit: Before half an hour I removed all splash-related packages w/o problems. Everything is normal but there is a strange behavior of /boot/grub/menu.lst. I removed from the 'kernel' line "quiet splash", but because of unknown reasons this part of line is still there during boot :-k

---

