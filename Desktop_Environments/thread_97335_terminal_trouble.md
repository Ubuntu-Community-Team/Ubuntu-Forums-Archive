---
title: "terminal trouble"
date: 2005-11-30
forum: Desktop Environments
---

### Post by crzyalien on 2005-11-30
im a noob and i am trying to install progams with the terminal. right now i am trying to install a .tar.gz file. i typed in the command

sudo dpkg -i **the file name**.tar.gz

it then asks for a password and i can not type it in.  the only key that works is enter.
sugestions?

---

### Post by Sutekh on 2005-11-30
When you type in your password you won't see any asterisks if that's what you mean, but it is still typing.

---

### Post by super on 2005-11-30
you cannot install tar.gz packages with dpkg. the only files dpkg will install are .deb files.

also, when you need to enter a password, just type it in and press enter. linux by default will not display the characters of the password on the screen.

what are you trying to install? it may be available via apt-get.

---

### Post by invalid on 2005-11-30
To install a tar.gz file, for whatever reason:
```
tar xvfz package.tar.gz
```
After this, search the newly extracted contents for a README file. This should give you some instructions that should look something like this:
```
make clean
make
make install
```
Be sure to check the file for specific details before you continue.

Some people use checkinstall within those directions, I personally don't, so if you want to go that route I suggest checking some man pages.

Cheers,
Invalid

---

### Post by rplantz on 2005-11-30
If you are new to Linux and are not a programmer, I recommend staying with installing .deb packages.

Many .tar.gz (or .tgz) packages install things in different places. It's not necessarily "wrong" but the .deb system keeps track of things, thus preventing duplications, etc. It's sorta like mixing accounting systems. If you know what you're doing and are very careful, it works. But it can also create a lot of headaches.

On the other hand, if a robust running system is not critical to you, and you enjoy learning new things, give it a try. There is a good discussion of the gnu programming tools at [http://autotoolset.sourceforge.net/tutorial.html](http://autotoolset.sourceforge.net/tutorial.html). It goes far beyond just learning how to install .tar.gz packages, but if you really want to understand what's going on, it's good. It's quite long, but this is a complex subject.

---

