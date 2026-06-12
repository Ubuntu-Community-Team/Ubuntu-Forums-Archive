---
title: "How to create a debian package?"
date: 2010-07-25
forum: Desktop Environments
---

### Post by Huzi94 on 2010-07-25
Hello,
I have successfully compiled Filezilla (Client) and now I would like to create a debian package whereby I can distribute the Software to my friends. Please can you give me some useful resources which will help me to create a debian package?

---

### Post by KdotJ on 2010-07-25
I refer you to [THIS]("http://ubuntuforums.org/showthread.php?t=910717") thread here. But to be honest, packaging is something you'll have to read up on

---

### Post by SlidingHorn on 2010-07-25
there's a lot to it.  Take a look through the packaging guide:

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by PaulReaver on 2010-07-25
install check-install

one way of compiling a deb would be similar to 
$./configure 
$make
$check-install

Its a slightly dumbed down version of events but it'll give you the gist.
have a read up on check-install.

hope it helps.

---

### Post by nilarimogard on 2010-07-26
Using checkinstall, you'll get a .deb package but without any dependencies so if the person who tries to install it doesn't have all the dependencies installed, it will not work. I wrote a quick [how-to on creating a debian package (.deb)]("http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html"), but that's for debianizing the package and in this case, you  don't have to debianize the package - that would take a lot of time and it's not required since filezilla has already been debianized in the ubuntu repositories. Try this:

1. Get the Filezilla source from Ubuntu - this includes the "debian" folder which is the debianization of this package:
```
sudo apt-get source filezilla
```2. Now download the filezila version you want to create a .deb for, and place the debian folder from the filezilla source you got in step 1, in this filezilla version. Make sure you change the filezilla version in debian/changelog according to the new version you downloaded and want to create a .deb file for.

Also make sure you have all the packages required to compile filezilla:
```
sudo apt-get build-dep filezilla
```3. Create the deb:

"cd" into the filezilla folder (for the filezilla version you want to create a .deb) and run:
```
    dpkg-buildpackage -rfakeroot -us -uc
```**If this seems to complicated, search for a Filezilla PPA!**

---

### Post by PaulReaver on 2010-07-26
maybe? if you just hit return at every question.

you can specify dependencies.  like I said "Its a slightly dumbed down version of events"

---

### Post by Wiid on 2010-07-26
I needed some stuff on this, So yeah it was pretty helpful.

---

