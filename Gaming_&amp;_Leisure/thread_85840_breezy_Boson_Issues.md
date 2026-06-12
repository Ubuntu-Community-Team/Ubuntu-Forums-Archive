---
title: "breezy Boson Issues"
date: 2005-11-03
forum: Gaming &amp; Leisure
---

### Post by uberlinux on 2005-11-03
Synaptic won't work with me on this, won't let boson install.  Whats the deal?

---

### Post by daller on 2005-11-14
A little debuggin information would be appreciated!

going to a console, try this:

sudo apt-get install boson

If I'm right, this is whats missing:

Dependency-problems on "boson-base, boson-data and boson-music"

...I don't know what to do on this...

...Try downloading the source, and compile it yourself...

---

### Post by cluelessnoob on 2005-11-15
I think i just downloaded the debian package and installed it.
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bison](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bison)

dpkg -i <package name> ?? I think


oops I thought you meant bison.... 

[http://packages.debian.org/unstable/games/boson](http://packages.debian.org/unstable/games/boson) 
Try this package

---

### Post by uberlinux on 2005-11-15
[QUOTE=daller]A little debuggin information would be appreciated!

going to a console, try this:

sudo apt-get install boson

If I'm right, this is whats missing:

Dependency-problems on "boson-base, boson-data and boson-music"

...I don't know what to do on this...

...Try downloading the source, and compile it yourself...[/QUOTE]
had the same problem, 
then it wouldnt compile.
figures, this is the first time that I ever got 3d working, so the one thing I got it working for dosent work...

---

