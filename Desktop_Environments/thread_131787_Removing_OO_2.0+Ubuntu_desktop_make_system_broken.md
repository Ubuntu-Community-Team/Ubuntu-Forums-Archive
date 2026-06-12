---
title: "Removing OO 2.0+Ubuntu desktop make system broken???"
date: 2006-02-17
forum: Desktop Environments
---

### Post by vn7xmen on 2006-02-17
Dear all
I have installed abiword, gnumeric, thunderbird, therefore I want to remove Open Office and Evolution. But when I choose remove OO and Evolution, it requires to remove 'ubuntu desktop'. I don't know exactly what is 'ubuntu desktop' and I am afraid that removing it make system brocken. Could you tell me how to remove safely OO and Evolution.
Thanks for supporting.
Regards

P/S: Because I am a newbie, so I don't undestand so much about Linux and Ubuntu. Pls forgive if this is a stupid question.

---

### Post by timetunnel on 2006-02-17
From the description of the "ubuntu-desktop" package:

> This package depends on all of the packages in the Ubuntu desktop system. It is safe to remove this package if some of the desktop system packages are not desired. However, it is recommended that you keep it installed, because it is used to carry out certain upgrade transitions (such as adding new packages to the system). 

This means: uninstalling ubuntu-desktop should not break your system (I haven't tried myself so far). This package contains no files at all (except for two informational files), it is just a collection of dependencies to other packages. However, it's possible that an upgrade to newer ubuntu versions needs formerly uninstalled or new packages to be installed. These new packages would be added to the ubuntu-desktop package as a dependency by the ubuntu team and you would get these new packages automatically. If you uninstall ubuntu-desktop, you will not get them and an upgrade might be more difficult (or not possible as all). 

Jens

---

### Post by timetunnel on 2006-02-17
...and if you're rather new to ubuntu I'd keep that package and wouldn't worry about the disc space needed by OOo or Evolution. Just ignore them.
Jens

---

### Post by Irony on 2006-02-17
I removed xsane which removed ubuntu desktop and I think yelp - and Ubuntu works fine.

I removed xsane because it was stopping Gimp from starting.

---

