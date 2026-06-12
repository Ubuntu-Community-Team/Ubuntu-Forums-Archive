---
title: "two questions about xfce"
date: 2023-11-01
forum: Desktop Environments
---

### Post by jarp53 on 2023-11-01
1- when I install xfce from the terminal in Ubuntu 23.10 , Am I installing xubuntu or the official xfce.

2- What is the developers recommendation on installing extra software , such as Wine,another browser, music player ,etc; Do I install all that first in Ubuntu then install xfce,or since I'm planning to use only xfce , do I do all of that in it .

---

### Post by Rubi1200 on 2023-11-01
I'm wondering why you don't just install Xubuntu if you want xfce?

To answer your questions, subjectively:

1. you are installing xfce not Xubuntu

2. don't think it makes a difference but probably better to add after installing xfce

Alternative suggestion:

create a new user, install xfce under the new user, at the login you can choose to use Ubuntu or xfce desktop.

---

### Post by jarp53 on 2023-11-01
thank for your info; and no I  have try xubuntu several times in the past only to be disappointed , but I already have install it, and it is great !!!!! here in 23.10 ; again thanks for your info.

---

### Post by vanadium on 2023-11-01
In Ubuntu, installing xfce will install the minimal xfce desktop. Installing `xubuntu-desktop`, however, will install the entire  xfce-desktop configured by the Xubuntu developpers, and also change the Plymouth theming and the login manager (LightDM instead of GDM). The experience will be similar as installing Xubuntu directly, except that the standard Ubuntu desktop and all of its applications are still on the system.

---

### Post by jarp53 on 2023-11-01
I think xfce runs better on Ubuntu 

[https://www.tecmint.com/install-xfce-desktop-ubuntu-linux-mint/](https://www.tecmint.com/install-xfce-desktop-ubuntu-linux-mint/)

---

### Post by vanadium on 2023-11-02
They adopted some of my key combinations, <Super>T for the terminal, <Super>W for the Browser,  <Super>E for the editor :P

---

### Post by ActionParsnip on 2023-11-02
1. The package will be xfce4 and only install the XFCE DE. The xubuntu-desktop package is a metapackage and installs a slew of packages that are default in Xubuntu. If you have applications already then you will duplicate functionality (you will install mousepad alongside gedit, for example).

2. Install packages as you see fit. I personally use apt but some prefer snap or flatpak. All are equally fine.

---

### Post by jarp53 on 2023-11-02
but if you install the full version of Ubuntu, install all the extra things you use; then add xfce desktop , you end with all  the best and fastest xfce out there and no xubuntu glitches . and  oh by the way it carries Ubuntu appearances and it looks fantastic !!!!

---

