---
title: "installing packages"
date: 2005-10-07
forum: Desktop Environments
---

### Post by qkmbr22 on 2005-10-07
i'm new to linux and i don't know how this works exactly, so i may be doing something wrong. When i try to install packages from [http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/) it sometimes works and sometimes doesn't... Like when i did "sudo apt-get install mozilla-firefox" and "sudo apt-get install gaim" it worked fine. But when i tried "sudo apt-get install 3dchess" or "sudo apt-get install gftp" it said "couldn't find package". why doesn't it install some packages?

---

### Post by invalid on 2005-10-07
The UbuntuGuide explains how to add repositories to your sources, so that all the packages can be available.

See:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

Cheers,
Cb

---

### Post by aysiu on 2005-10-07
If you use Synaptic Package Manager, you can browse and search for packages graphically--it's the same as apt-get but graphical.

---

### Post by ubuntumaneh on 2005-10-07
If you want (or feel better) with terminal and apt-get install, i suggest to use:

$ apt-cache search {name}

where name is the a possible name of a package. You can even output it to a file using:
$ apt-cache search {name} > {outputfile}

You can use this procedure for knowing the exactly name of the package to be apt-gotten.

---

### Post by qkmbr22 on 2005-10-08
i tried to add extra repositories just like it said in the ubuntuguide, but when i typed in "sudo gedit /etc/apt/sources.list", Konsole said "sudo: gedit: command not found"... why is this?

---

### Post by Adrian on 2005-10-08
[QUOTE=qkmbr22]i tried to add extra repositories just like it said in the ubuntuguide, but when i typed in "sudo gedit /etc/apt/sources.list", Konsole said "sudo: gedit: command not found"... why is this?[/QUOTE]

gedit is a Gnome editor which isn't included in KDE/Kubuntu. Just replace "gedit" with "kate" which is the KDE equivalent.

Edit: You might want use "kdesu" instead of "sudo", since the latter seems to give error messages in combination with kate for some users.

---

