---
title: "Switching Login Managers"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Dillius on 2005-10-14
I installed Ubuntu and then installed kubuntu-desktop from the package manager in order to give me access to either desktop software. It made me choose between kdm and gdm as my login manager, and I am wondering if there is an easy way to switch this later if I choose to?

---

### Post by rosslaird on 2005-10-15
Yup, it's easy:

sudo dpkg-reconfigure kdm (or gdm)

You can also then use rcconf to specify that the default one loads at startup.

You can also do this on the fly, using (from a virtual console, with gdm/kdm on another screen):

sudo /etc/init.d/kdm stop
rcconf (choose default login manager)
sudo /etc/init.d/gdm start
ctrl-f7

Hope that makes sense. It's not exactly intuitive, but it works.

Ross

---

