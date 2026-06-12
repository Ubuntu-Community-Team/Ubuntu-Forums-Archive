---
title: "where is the source?"
date: 2005-05-03
forum: Desktop Environments
---

### Post by metalhead1992 on 2005-05-03
hey, i cant seem to find the source... dose anyone know where i can get it & how to compile it + load it onto a computer once i make changes? thanks :)
i love this os, by the way, good job :D
~nLaQuet

---

### Post by -Rick- on 2005-05-03
Source for what? KDE? You can search for packages ending with '-dev' or '-devel', they contain the source code.

---

### Post by metalhead1992 on 2005-05-04
thanks :) yes - that was what i was looking for. do you know how to compile it?

---

### Post by az on 2005-05-04
[QUOTE=-Rick-]Source for what? KDE? You can search for packages ending with '-dev' or '-devel', they contain the source code.[/QUOTE]

No.  Those are the headers.

You have precompiled binary packages (deb) and you have the source packages.  The source repositories are the deb-src entries in your /etc/apt/sources.list

A binary package has three source files (sometimes two) a .dsc a .diff and an .orig.tar.gz

sudo apt-get build-dep <package>
sudo apt-get source <package>
That will install the source for <package> as well as all the packages needed for compilation.

Once compiled, if youneed to compile another application along with it, you can use the -dev packages created during the compilation (and packaged).  They do not contain the source, they contain the headers so that you can link stuff to the binaries.

---

### Post by wbeck85 on 2005-05-04
[QUOTE=azz]No.  Those are the headers.

You have precompiled binary packages (deb) and you have the source packages.  The source repositories are the deb-src entries in your /etc/apt/sources.list

A binary package has three source files (sometimes two) a .dsc a .diff and an .orig.tar.gz

sudo apt-get build-dep <package>
sudo apt-get source <package>
That will install the source for <package> as well as all the packages needed for compilation.

Once compiled, if youneed to compile another application along with it, you can use the -dev packages created during the compilation (and packaged).  They do not contain the source, they contain the headers so that you can link stuff to the binaries.[/QUOTE]
 Once you apt-get the sources, where are they put? I would assume that one could just navigate to the directory and then ./configure, make, make install ?

---

### Post by Tsjoklat on 2005-05-05
[QUOTE=metalhead1992]hey, i cant seem to find the source... dose anyone know where i can get it & how to compile it + load it onto a computer once i make changes? thanks :)
i love this os, by the way, good job :D
~nLaQuet[/QUOTE]

sudo adduser *user* staff
sudo adduser *user* src
log out/in
cd /usr/local/src
mkdir kde
cd kde
sudo apt-get build-dep kde
sudo apt-get install fakeroot
sudo apt-get install apt-src
apt-get source kde <-- You are added to the src group so no need for sudo
dpkg-source -x *nameofthefile*.dsc
cd *nameofthedir*
fakeroot dpkg-buildpackage <-- It is better to build a package without being root
cd ..
sudo dpkg -i *.deb
rm -rf *nameofdir*

This way you will have your own build kde.debs

D

---

