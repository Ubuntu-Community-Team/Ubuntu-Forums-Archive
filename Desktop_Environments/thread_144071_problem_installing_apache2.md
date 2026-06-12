---
title: "problem installing apache2"
date: 2006-03-13
forum: Desktop Environments
---

### Post by 1000i1 on 2006-03-13
Well, I installed apache2 with adept, but I also installed apache, so I wanted to keep onlye apache2. I removed apache, apache2, php5, and lots of things, and now I want them back, so I open adept, select apache2, php5 and so on, and they don't seem to get installed correctly, I get the apache 2 without the /etc/apache2.conf, and the foldres /etc/apache2/available-modules and /etc/apache2/enabled-modules are empty, I've tried to reinstall all the neede files a hundred times, using adept or by command line, but I can't get a proper installation, anyone knows what might be happening?? Thxs in advanced.

---

### Post by Koybe on 2006-03-13
Try to reinstall the packages you need with :

```
sudo apt-get --reinstall install package
```

---

### Post by 1000i1 on 2006-03-13
It doesn't work, I can't understand it, and I'm starting to get really pissed off, it worked fine this morning!!!

---

### Post by Koybe on 2006-03-14
Try this :
```
dpkg -l apache2*
dpkg -l libapache2*
```
It should give you a list of packages. When you got ii in front of the line, it means this package is installed. 

Then try removing every installed package with dpkg.

```
dpkg -P package 
```

And then, restart your installation.

Hope it will work. GL.

---

### Post by adamkane on 2006-03-14
It's very difficult to un-install Apache 1.3, and install Apache2. You need to choose one or the other, and stick with that choice.

---

### Post by 1000i1 on 2006-03-14
Thanks Koybe that worked great, I uninstalled using adept or apt-get remove, but in dpkg -l I've seen they were still installed or something strange, and after a while uninstalling and reinstalling I've got it working again, now let's see if the php5 module works, thanks.

---

