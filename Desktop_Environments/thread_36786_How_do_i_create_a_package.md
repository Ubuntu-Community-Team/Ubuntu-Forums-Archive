---
title: "How do i create a package?"
date: 2005-05-24
forum: Desktop Environments
---

### Post by z-vet on 2005-05-24
Hi all. 
Simple question: how do i make my own package from sources?

---

### Post by Xian on 2005-05-24
You mean make a .deb file for your system?

Install [checkinstall](http://asic-linux.com.mx/~izto/checkinstall/) using Synaptic and then issue the build commands provided in the install file which should be a part of the source package. Generally this would include:

```
$ ./configure
$ make
$ sudo checkinstall
```

---

### Post by philipacamaniac on 2005-05-25
[QUOTE=Xian]You mean make a .deb file for your system?

Install [checkinstall](http://asic-linux.com.mx/~izto/checkinstall/) using Synaptic and then issue the build commands provided in the install file which should be a part of the source package. Generally this would include:

```
$ ./configure
$ make
$ sudo checkinstall
```[/QUOTE]
 Just a note, when making debian packages with checkinstall, the default location to install KDE applications is /usr/local/kde, but Kubuntu (and Ubuntu) use /usr/local. I don't know if there is a way to configure checkinstall to change this behaviour, but my workaround for my own systems is to create a symbolic link /usr/local/kde/ that points to /usr/local.

Might consider that before creating checkinstall packages. I think over in the development forums you can find alternative methods for creating packages.

---

### Post by z-vet on 2005-05-25
Ok, thanks.

---

### Post by vanaedium on 2005-05-25
./configure --prefix=/usr
make 
sudo checkinstall

and if you open synaptic you'll see a group called checkinstall and you'll see every packages you create with checkinstall

---

