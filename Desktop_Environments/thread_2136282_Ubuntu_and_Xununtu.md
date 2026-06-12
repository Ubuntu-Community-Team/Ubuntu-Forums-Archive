---
title: "Ubuntu and Xununtu"
date: 2013-04-17
forum: Desktop Environments
---

### Post by bigdes on 2013-04-17
Hi 
Just wondering could anybody point me in the right direction. My hard drive packed up and had to get a replacement trying to get my old operatin system back just can't remember how to do it. I'm after Ubuntu + Xfce = Xubntu were I had the option off logging in to either one of these desktop environments. So if anybody can point me in the right direction of the commands to excucute this programme from the terminal I would greatly appreciate it.

Des :(

---

### Post by Lars Noodén on 2013-04-17
Well you could install one from CD/DVD and then add the other using apt-get.  For example, if you have installed Ubuntu already then the following will add Xubuntu:

```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```

Or do the reverse, start with Xubuntu and add Ubuntu-desktop.  That will give you both distros.  

If you want only the XFCE desktop environment then that package is **xfce4** and xubuntu-desktop is not needed.

---

### Post by bigdes on 2013-04-19
Thanks mate your post helped me to remember. I was running on xubuntu needed desktop enviorrnment for ubuntu.So here is a command for anybody that is running on xubuntu that is looking ubuntu desktop enviorrment.

---

### Post by bigdes on 2013-04-19
Thanks mate your post helped me to remember. I was running on xubuntu needed desktop enviorrnment for ubuntu.So here is a command for anybody that is running on xubuntu that is looking ubuntu desktop enviorrment.  


[B]
sudo apt-get update 
[/B]
**sudo apt-get install ubuntu-desktop**Quote



Sorry for the typing error in command 100% now:

---

