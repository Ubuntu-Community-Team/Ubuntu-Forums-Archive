---
title: "Dofus wont launcher: missing libs"
date: 2011-07-16
forum: Gaming &amp; Leisure
---

### Post by Purplerob on 2011-07-16
I installed dofus on 64 bit 11.04 Ubuntu. But I know it uses some 32 bit libraries. When I launch it from the menu I get nothing. When I launch in terminal with ./launch-dofus.sh (in the dofus folder.) It tells me 
```
error while loading shared libraries: libgobject-2.0.so.0: cannot open shared object file: No such file or directory

```
When I use Uplauncher I get 
```
libgthread-2.0.so.0: cannot open shared object file: No such file or directory

```
I put both these libs in getlibs and it tries to install libglib2.0-0
But I still get the same error

---

### Post by Purplerob on 2011-07-16
Found the location of the files. Is there anyway to direct dofus there?

---

### Post by Perfect Storm on 2011-07-16
You need to install the 32-bit version of the missing libs to /usr/lib32 and not /usr/lib (which are 64-bit libs place).

You can't uses the libs in /usr/lib to run 32-bit applications.

---

### Post by Elaztic on 2011-08-18
Hi, did you manage to solve it?
If we have (had) the same issue then running dofus from the terminal will give you an error message that contains this:
> wrong ELF class: ELFCLASS64

Anyway...this is how I got Dofus working on 64-bit Ubuntu 11.04 (Gnome, not Unity if that makes any difference) on AMD Athlon X3 (homebrew) machine.

First install known dependencies/prerequisites (I am not 100% sure they are really needed but it was suggested in this thread: [http://machinarium.net/forum/index.php?PHPSESSID=736546db2bd8d8a3805ce9611cf40e26&topic=1227.msg5946#msg5946):](http://machinarium.net/forum/index.php?PHPSESSID=736546db2bd8d8a3805ce9611cf40e26&topic=1227.msg5946#msg5946):)

```
sudo apt-get install curl
```
```
sudo apt-get install ia32-libs
```

Then follow this guide ([http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/]("http://www.jamesward.com/2010/10/14/install-adobe-air-on-64-bit-ubuntu-10-10/")) to install Adobe Air since it is a prerequisite for installing and running Dofus. I followed the 7 steps James describes.

Then download and install the latest version of dofus from [www.dofus.com]("http://www.dofus.com") (If you are a GUI person then right-click on the dofus install file and choose properties - permissions and check the box in front of 'Allow executing file as program' and click 'OK'. Double-click to install it).

Hopes this solves it for you :)

---

