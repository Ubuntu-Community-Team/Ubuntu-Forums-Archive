---
title: "Error everytime i try to intall a program"
date: 2007-11-23
forum: Desktop Environments
---

### Post by lacandu on 2007-11-23
E: Couldn't find package - i get this error everytime i try to install a program why? how can it be easier to intall a program im fairly new to ubuntu linux

---

### Post by bonzodog on 2007-11-23
Exactly what method are you using to install the package?

Are you using 
```
sudo apt-get install <packagename>
```?

if you are, it could be that the package name needs to be a little more exact

Out of interest, what package do you want to install, and on which release?

It might be worth doing a search to check for the package using synaptic (the GUI front end).

---

### Post by lacandu on 2007-11-23
im trying to install from terminal using sudo apt-get install name of the package, the packege is a theme for the background,

---

### Post by jhenager on 2007-11-23
Try this:
On the Applications menu, click Add/Remove.
Enter your password when prompted.
Under Other, look for Art Manager and install it.

---

### Post by bonzodog on 2007-11-25
> **lacandu said:**
> im trying to install from terminal using sudo apt-get install name of the package, the packege is a theme for the background,

um...quick question.

have you already downloaded this package?

see, apt-get install actually downloads packages from the repos, and then installs them.

To install an already downloaded .deb package you need to use dpkg -i <packagename>, or even easier, browse to the package in nautilus, right click on it, and then click 'install this package'(or whatever term it uses. Not used nautilus for a long time)

However, to obfuscate things a little more, themes don't come as packages, they come in .tar.gz form normally from sites like gnome-look.org. All you do with them is simply untar (tar -xvzf <themename.tar.gz>) them into your ~/.themes dir, and the theme manager will see them then.

---

