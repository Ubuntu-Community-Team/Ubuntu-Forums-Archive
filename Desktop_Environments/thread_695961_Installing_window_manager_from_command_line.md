---
title: "Installing window manager from command line"
date: 2008-02-13
forum: Desktop Environments
---

### Post by xelapond on 2008-02-13
I have gotten kind of annoyed by how many programs come standard with Ubuntu(Compiz, Graphics stuff, Games, etc) that I will never use.  I figured the best way to fix this problem would just be to install a bare Ubuntu server, and install everything from there.

What packages would I need to install to get KDE4.0.1 running on a bare Ubuntu Server install?

Thanks, 

Alex

---

### Post by ola on 2008-02-13
Hi!

There is a package called kde4base that you can install with:

sudo apt-get install kde4base

you might also want to install kdm (the graphical login program for KDE) with

sudo apt-get install kdm

---

### Post by xelapond on 2008-02-13
Thanks, 

What packages do I need to install for the X-Server?

Thanks again, 

Alex

---

### Post by honeydew on 2008-02-13
I would imagine the xserver is a dependency of kde but if not 

apt-get install xserver-xorg

should do the trick.

---

### Post by xelapond on 2008-02-13
Thanks, 

Just one final question, do I need to add any repositories or anything to get the stable version of KDE4.0.1, or is it in the main Ubuntu repository?

---

### Post by honeydew on 2008-02-14
Im not sure what version of ubuntu you are using but you can use aptitude to give you this info,

aptitude show kdebase

for me in hardy heron:

```

austin.trask@underling:~/lat-1.2.3$ aptitude show kdebase
Package: kdebase
State: not installed
Version: 4:3.5.8-2ubuntu20
Priority: optional
Section: kde
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 106k
Depends: hal | kfreebsd-gnu | hurd, kappfinder (>= 4:3.5.8-2ubuntu20), kate (>= 4:3.5.8-2ubuntu20), kcontrol (>= 4:3.5.8-2ubuntu20), kdebase-bin (>=
         4:3.5.8-2ubuntu20), kdebase-data (>= 4:3.5.8-2ubuntu20), kdebase-kio-plugins (>= 4:3.5.8-2ubuntu20), kdepasswd (>= 4:3.5.8-2ubuntu20), kdeprint (>=
         4:3.5.8-2ubuntu20), kdesktop (>= 4:3.5.8-2ubuntu20), kfind (>= 4:3.5.8-2ubuntu20), khelpcenter (>= 4:3.5.8-2ubuntu20), kicker (>=
         4:3.5.8-2ubuntu20), klipper (>= 4:3.5.8-2ubuntu20), kmenuedit (>= 4:3.5.8-2ubuntu20), konqueror (>= 4:3.5.8-2ubuntu20), konqueror-nsplugins (>=
         4:3.5.8-2ubuntu20), konsole (>= 4:3.5.8-2ubuntu20), kpager (>= 4:3.5.8-2ubuntu20), kpersonalizer (>= 4:3.5.8-2ubuntu20), ksmserver (>=
         4:3.5.8-2ubuntu20), ksplash (>= 4:3.5.8-2ubuntu20), ksysguard (>= 4:3.5.8-2ubuntu20), ktip (>= 4:3.5.8-2ubuntu20), kwin (>= 4:3.5.8-2ubuntu20),
         libkonq4 (>= 4:3.5.8-2ubuntu20)
Recommends: kdm (>= 4:3.5.8-2ubuntu20)
Suggests: kdebase-doc-html (>= 4:3.5.8-2ubuntu20)
Description: base components from the official KDE release
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines ease of use, contemporary
 functionality, and outstanding graphical design with the technological superiority of the Unix operating system. 
 
 This metapackage includes the nucleus of KDE, namely the minimal package set necessary to run KDE as a desktop environment. This includes the window
 manager, taskbar, control center, a text editor, file manager, web browser, X terminal emulator, and many other programs and components.

```

---

