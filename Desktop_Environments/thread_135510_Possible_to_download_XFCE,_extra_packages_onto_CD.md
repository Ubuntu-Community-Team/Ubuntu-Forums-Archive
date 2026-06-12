---
title: "Possible to download XFCE, extra packages onto CD?"
date: 2006-02-24
forum: Desktop Environments
---

### Post by NewGroove on 2006-02-24
Hi, I have a (probably dumb) question, but is it possible to download XFCE and extra programs that don't come with the standard Gnome packages from Ubuntu... and then burn them to a CD so I don't have to download them again when I reinstall Ubuntu? What steps would I have to do (like commands & stuff)? And once I have them on CD, how would I go about installing them from the CD instead of the internet?

Appreciate any help you could give,
Mike

---

### Post by nanotube on 2006-02-24
you can get all the packages in .deb format from [http://packages.ubuntu.com](http://packages.ubuntu.com)
then burn all the .debs to cd
then, to install them, use command "dpkg -i". eg:
```
sudo dpkg -i somepackage.deb
```

---

### Post by nanotube on 2006-02-24
oh, and by the way, if you have already installed these packages with apt-get or synaptic on your current system, all the .deb files will be in /var/cache/apt
so you can just burn that entire directory to cd and have all the .debs you need. :)

---

### Post by az on 2006-02-24
This page was originally for that:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by nanotube on 2006-02-25
oh hey, thats a cool link, azz.

---

### Post by aysiu on 2006-02-25
Is anyone willing to host an .ISO of Ubuntu extras like XFCE?

Didn't we used to have an extras CD somewhere around here?

This is a very popular request, especially from those without an internet connection on their Ubuntu computers and those who have dial-up.

---

