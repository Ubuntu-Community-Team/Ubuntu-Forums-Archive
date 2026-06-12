---
title: "I cannot open add/remove"
date: 2008-07-17
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-17
In xubuntu on my desktop, when I click on add/remove , I get the following message:
The application need special administrative privileges. Please run it as root or through kdesu or sudo program. Please help.

---

### Post by benerivo on 2008-07-17
You can run anything as root as long as you know the package name. I think the gnome application installer is called gnome-app-install. I don't know if this is the same add/remove program that you have in xubuntu, but if it is then you can open a terminal and enter```
gksudo gnome-app-install
```if this doesn't work then try```
sudo gnome-app-install
```

---

### Post by mirchichamu on 2008-07-17
> **benerivo said:**
> You can run anything as root as long as you know the package name. I think the gnome application installer is called gnome-app-install. I don't know if this is the same add/remove program that you have in xubuntu, but if it is then you can open a terminal and enter```
gksudo gnome-app-install
```if this doesn't work then try```
sudo gnome-app-install
```

Thanks for your support. It worked as you advised but when I closed I got the same message. While in my laptop this is not the case. In my laptop I can always open add/remove program.

---

### Post by benerivo on 2008-07-17
So the program works okay now, but when you close it, it tells you that it needs special administrative privileges? Are you still able to install/remove apps using it?

I don't know why it tells you that it needs admin priviges. There are several 'package managers' for ubuntu. Some of them open normally for anyone (as this one should) and only need a password when you actually try to remove or add a package. Others (like synaptic) ask you for a password when you first open them.

---

### Post by mirchichamu on 2008-07-17
> **benerivo said:**
> So the program works okay now, but when you close it, it tells you that it needs special administrative privileges? Are you still able to install/remove apps using it?

I don't know why it tells you that it needs admin priviges. There are several 'package managers' for ubuntu. Some of them open normally for anyone (as this one should) and only need a password when you actually try to remove or add a package. Others (like synaptic) ask you for a password when you first open them.

Thanks a lot once again. It asked for it when opened it again. But I found Gnome add/remove and it working well. Thanks again for support and helping>.One million thanks.

---

