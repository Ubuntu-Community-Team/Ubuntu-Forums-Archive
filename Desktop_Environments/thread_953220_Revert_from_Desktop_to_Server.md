---
title: "Revert from Desktop to Server"
date: 2008-10-19
forum: Desktop Environments
---

### Post by pawnrocket on 2008-10-19
Is it possible to revert from Ubuntu Desktop 8.04-1 to Ubuntu Server? :confused:

Also the icon, you know the ubuntu one on the menu. I would like to replace it with my own. Any ideas?

---

### Post by Rhubarb on 2008-10-19
If you want to revert from Desktop to server, you'd have to uninstall a lot of software (Ubuntu Server does not have gnome, it's all text based).
If you just want to leave your Desktop as-is, but want to do some common server tasks, then load up Synaptic Package Manager (System --> Administration --> Synaptic)
Edit --> Mark Packages by Task, then choose what services you wish to install.

I'm not sure exactly how one would go about removing the desktop, and getting a default ubuntu-server install from a Desktop install.

The Ubuntu icon (top-left) for the Human theme can be found here:
/usr/share/icons/Human/scalable/places/start-here.svg

---

### Post by p_quarles on 2008-10-20
As Rhubarb said, there isn't any kind of absolute difference between the editions, they're just collections of packages. If you are looking for certain functionality, specify what you need and we can help you get there.

---

