---
title: "Completely removing Ubuntu Desktop"
date: 2007-05-22
forum: Desktop Environments
---

### Post by bg1256 on 2007-05-22
Hello all,

I have Kubuntu Feisty installed, and I installed ubuntu-desktop through the command line last night, just to play with Gnome again.

However, I realized I just prefer KDE better.

I ran the following:

sudo apt-get remove ubuntu-desktop


But I still have all the Gnome programs installed.

Is there a way to remove them all by running one command?


Thanks in advance!

---

### Post by atoponce on 2007-05-23
ubuntu-desktop is just a meta package to describe to the system all the other packages that need to be installed.  If you want a pure KDE system, [then follow this tutorial]("http://psychocats.net/ubuntu/purekde") to remove all the Gnome programs.

---

### Post by AnRa on 2007-05-23
If you installed using this command:
```
sudo apt-get install ubuntu-desktop
```
then you have to use:
```

sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove

```
That should remove all the unnecesary packages. ;)

---

