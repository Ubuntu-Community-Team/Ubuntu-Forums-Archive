---
title: "ubuntu with kubuntu"
date: 2010-04-06
forum: Desktop Environments
---

### Post by SOME1 on 2010-04-06
Hi, 

I have ubuntu 9.10 om my computer and windows xp. I want to install kde desktop with gnome desktop. 
I know that I can install it using the command 
```
sudo apt-get install kubuntu-desktop
```

the thing is, that from what I understand after install kubuntu with ubuntu, all kde programs will be also on the gnome menus and that's what I don't want to happend. 

Is there any way to install kde with gnome but without the programs will mix in the menus? 

if not, how can I install kubuntu side by side with ubuntu so when grub is load I will decide if I want to load ubuntu or kubuntu. 

thanks.

---

### Post by conradin on 2010-04-06
hm, my Understanding is that you will have the option to log into KDE or gnome at login. Thats how it was in RHEL3 and everything else Ive ever used. Just for giggles Ill try it right now. 1 sec.

---

### Post by SOME1 on 2010-04-06
yes, but I have that option in gdm not in grub. it's great that it's there but all kde programs is in gnome menus in this case.

thanks.

---

### Post by lovinglinux on 2010-04-06
Install [kde-minimal](apt:kde-minimal) and [kdeplasma-addons](apt:kdeplasma-addons) [apt-get].

This is what I use and it works great. You might need to install additional packages later, depending on what you need. Nevertheless, I would recommend several KDE applications, which are far better than Gnome IMO.

You might also use the [kubuntu backports ppa](https://launchpad.net/~kubuntu-ppa/+archive/backports/), to get KDE 4.4, which is awesome.

---

