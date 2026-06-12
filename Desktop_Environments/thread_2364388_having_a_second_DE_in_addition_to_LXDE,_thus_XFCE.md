---
title: "having a second DE in addition to LXDE, thus XFCE"
date: 2017-06-22
forum: Desktop Environments
---

### Post by francois.e on 2017-06-22
How do I install XFCE4 as a second DE for lubuntu xenial? Is it:
[https://forum.ubuntu-fr.org/viewtopic.php?id=993881](https://forum.ubuntu-fr.org/viewtopic.php?id=993881)
```

sudo apt-get install xubuntu-desktop 
```
[https://askubuntu.com/questions/179148/set-default-user-session-to-xfce4](https://askubuntu.com/questions/179148/set-default-user-session-to-xfce4)
```
sudo apt install xubuntu-default-settings

```

---

### Post by francois.e on 2017-06-22
And back into lightdm login manager:
select xfce4

---

### Post by deadflowr on 2017-06-22
Why not just install xfce4?
xubuntu-desktop will install the xubuntu desktop, which includes a few extras do-dads.

---

### Post by francois.e on 2017-06-22
Answer:
There was a problem installing xfce with the iso. And as I was trying lubuntu to see how much performant on my old MSI-340x laptop, I realized that xfce offers much with less pain. In addition, I could revert to lxde DE if so is my wish.

Edited first post to include usb auto-mount packages gvfs and thunar-volman.

---

### Post by deadflowr on 2017-06-22
What ISO?

---

### Post by Bucky Ball on 2017-06-23
```
sudo apt install xfce4
```

That is all if you want to install xfce. You do NOT want to install xubuntu-desktop. That is equivalent to installing Xubuntu on top of your current OS. Not great. You only want the DE.

---

