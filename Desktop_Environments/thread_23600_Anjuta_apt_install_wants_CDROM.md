---
title: "Anjuta apt install wants CDROM???"
date: 2005-04-03
forum: Desktop Environments
---

### Post by b7j0c on 2005-04-03
$ sudo apt-get install anjuta
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  anjuta-common libpcre3
Suggested packages:
  libgtkmm2.0-dev libgnomemm2.0-dev devhelp-books glade-2 glade-gnome-2
Recommended packages:
  automake autoconf autogen ctags devhelp gnome-devel libtool
The following NEW packages will be installed:
  anjuta anjuta-common libpcre3
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6628kB/6735kB of archives.
After unpacking 14.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter



???????

why does this package install want the installation media (which i have loaned out) ??

---

### Post by prio on 2005-04-04
Might seem obvious but have you changed your /etc/apt/sources.list? It should read something like the following.

-- Cut here --
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
-- Cut here --

Notice the # in front of the cdrom entry and the # removed from the other lines. Once you have saved this as /etc/apt/sources.list run
  apt-get update
and then 
  apt-get install anjuta

---

