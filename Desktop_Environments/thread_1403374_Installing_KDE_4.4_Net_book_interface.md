---
title: "Installing KDE 4.4 Net book interface"
date: 2010-02-10
forum: Desktop Environments
---

### Post by WinterMadness on 2010-02-10
does anyone know how to do this?

Thanks

[http://kde.org/workspaces/plasmanetbook/](http://kde.org/workspaces/plasmanetbook/)

---

### Post by Zorael on 2010-02-11
There is a **plasma-netbook** package in the Karmic repositories, but it's only a tech preview and could be buggy. Nevertheless, you should be pretty set after merely installing that, though you may run into issues where both plasma desktop and plasma netbook are started upon login.

The real first release of plasma netbook is in KDE SC 4.4, of which you can get (unsupported) packages from the Kubuntu backports ppa (**[ppa:kubuntu-ppa/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)**).

---

### Post by kombipom on 2010-02-14
OK, so I added the ppa
```
sudo add-apt-repository ppa:kubuntu-ppa/backports
```
updated apt
```
sudo apt-get update
```
then tried to install plasma-netbook
```
sudo apt-get install plasma-netbook
```
but I get an error
```
plasma-netbook: Depends: kdebase-workspace-bin (>= 4:4.4.0) but it is not going to be installed
```

Presumably there is a good reason why it didn't install it.

I'm trying to add kde4-netbook as an alternative (choose at boot).  I have Karmic netbook edition at the moment.

Anybody managed this?  Any advice?

---

### Post by Zorael on 2010-02-14
The ppa contains KDE SC 4.4, which includes plasma-netbook 4.4. Upgrading to plasma-netbook 4.4 also requires the rest of KDE to be at 4.4.

```
$ sudo aptitude update
$ sudo aptitude full-upgrade
$ sudo aptitude install plasma-netbook
```

Beware that you might run into a bug that restarts X when upgrading, so don't do anything critical when the second command is running. (I'm not sure if it's fixed yet.)

If you don't want to take the leap and upgrade to 4.4, just remove the ppa from your sources list and install the official repository tech preview version (of plasma-netbook).

---

