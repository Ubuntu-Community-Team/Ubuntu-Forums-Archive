---
title: "ubuntu to xubuntu"
date: 2008-12-23
forum: General Help
---

### Post by hockey6611 on 2008-12-23
i have a persistent live ubuntu installation on a usb drive and i want to change it to a xubuntu installation 

how would i go about doing this 

also how would i expand the wubi virtual drive

---

### Post by magmon on 2008-12-23
As far as ubuntu to xubuntu, I think your going to need to uninstall ubuntu and install xubuntu.

For expanding wubi, [this is the only option I know of.]("http://ubuntuforums.org/showthread.php?t=438591")

---

### Post by Liviu-Theodor on 2008-12-23
You could also install xubuntu-desktop and make it default. If you want to, you can also uninstall ubuntu-desktop, to make the change permanent, or you can keep them both and at login time, you can chose on which desktop to work.

---

### Post by nordmichael29 on 2008-12-23
you can install xubuntu through aptitude, the only doiwnside I'm aware of is that the ubuntu installation is still there. you can still boot using the ubuntu kernal, you can later remove this also through aptitude.

---

### Post by hockey6611 on 2008-12-23
if i install xubuntu how would i import all of my files/settings/programs/etc.

---

### Post by Liviu-Theodor on 2008-12-23
If you have the [FONT="Courier New"]/home[/FONT] partition separate, then there is no trouble, just do NOT format it and declare it again in the xubuntu installation. If not, you could either back it up and restore it under xubuntu, or you could reorganize your partitions under ubuntu and make it separate, and after that is the first case.

---

### Post by dannytatom on 2008-12-23
> **hockey6611 said:**
> i have a persistent live ubuntu installation on a usb drive and i want to change it to a xubuntu installation 

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
Copy & paste the part that says "Remove Ubuntu," it'll remove gnome & all the apps that come with it, and install xfce + lightweight apps (like a fresh install of xubuntu).

---

