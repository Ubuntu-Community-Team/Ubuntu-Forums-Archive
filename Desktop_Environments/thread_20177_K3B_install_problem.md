---
title: "K3B install problem"
date: 2005-03-15
forum: Desktop Environments
---

### Post by Amdmhz on 2005-03-15
Hi everyone. I decided to try out Ubuntu last night. Very nice Distro. Everything is fine except for a CD Burning Program. I am use to K3B so I decided to apt-get that. When I go to install it , it tells me a depend will not be installed and a depend that is not installable? Is there a different Repository that I need to go to for this program to install properly? I really need this CD Burning program. [-o< 

Thanks
Amdmhz

---

### Post by theChauvinist on 2005-03-15
I'm a newbie, so you might want to ignore me, but I think K3B is dependent on the KDE desktop, whereas Ubuntu by default uses GNOME. So, you can't use K3B under it.

You can install KDE and GNOME, as I did when I was using Fedora but it slows things down considerably. The options seem to be to use a different program, such as gnomebaker, to use KDE (which isn't supported on Ubuntu) or to use a different distro.

---

### Post by LongTooth on 2005-03-15
There are now two CD burning app you can use without installing a KDE libs. They are Graveman and Gnomebake. Both are able to be downloaded via the apt-get command or with Synaptic. Check them out before installing K3B.

---

### Post by Amdmhz on 2005-03-16
hi and thanks for the replies. I did an apt-get on both of those files and I get "couldn't find package" Is there more sites I should put in my sources.list file that I don't know about? Here is my current list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://www.planet-moll.de/debian](http://www.planet-moll.de/debian) woody main
deb [http://www.planet-moll.de/debian](http://www.planet-moll.de/debian) sarge main

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

Thanks for the help
Amdmhz

---

### Post by LongTooth on 2005-03-16
I should have mentioned that I'm using Hoary. I would suggest you upgrade to Hoary. Both of these CD burning packages are in the Hoary repositories. Comment out (#) the added repositories you've added and then update, upgrade, dist-upgrade to Hoary. You will then be able to install Gnomebaker or Graveman. There might be something in the Warty backports. You'll have to look that up yourself. 

I've dist-upgraded to Hoarty and have not had a problem at all. I think it's stable enough for anyone to do it. BUT, comment out the extra repositories you've added to Warty.

---

### Post by WW on 2005-03-16
k3b is available in the universe repository in warty, and it works fine.  What error did you get when you tried to install it?

---

### Post by iomicifikko on 2005-03-16
[QUOTE=WW]k3b is available in the universe repository in warty, and it works fine.  What error did you get when you tried to install it?[/QUOTE]
 exactly it works fine even in gnome, u simply have to install also some kdelibraries, but apt-get/synaptic will do it for u.

follow this guide to avoid a few problems using k3b in ubuntu:

[https://www.ubuntulinux.org/wiki/K3BHowto](https://www.ubuntulinux.org/wiki/K3BHowto)

bye

---

### Post by Amdmhz on 2005-03-16
Hi all. sorry for the delay. Here is the error message I get.

The following packages have unmet dependencies:
k3b: Depends: k3blibs (>= 0.11.19) but it is not going to be installed
Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable

Thanks for the help.

Amdmhz

---

