---
title: "Installing Synaptic (solved)"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Wheelie on 2005-10-26
How do i do :confused:  when i am installiing a program and it stands like this:


 1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.


Where do i write that codes? It stands what i can write, but not where? 
tell me please!  :KS

---

### Post by endersshadow on 2005-10-26
You're supposed to run those commands in the terminal (Applications>Accessories>Terminal in Breezy).

However, I have to ask, what program are you trying to install?

And how new are you to Linux?

---

### Post by RAOF on 2005-10-26
The best way to install a program is through Synaptic.  Search for the program you want to install, select it, hit apply, then watch it download, install, and configure itself for you :)

That will work for anything in the repositories, and if you've enabled the universe/multiverse repositories, that includes practically everything.

---

### Post by aysiu on 2005-10-26
Yes, please mention the name of the program you're trying to install. It's very likely there's a far easier way to install it than what you're trying to do.

---

### Post by Wheelie on 2005-10-26
[QUOTE=RAOF]The best way to install a program is through Synaptic.  Search for the program you want to install, select it, hit apply, then watch it download, install, and configure itself for you :)

That will work for anything in the repositories, and if you've enabled the universe/multiverse repositories, that includes practically everything.[/QUOTE]

Im trying to install Synaptic!
I installed Linux yesterday and havent been on a Linux computer ealrier :P
IM quite good to learn fast, so i think i can make it! I dont now what to write in the terminal to come to that folder who that program is in! The terminal cant now what i mean if i writes that things, if it dont now where the installation file is, aint i right?

Please help me!

---

### Post by aysiu on 2005-10-26
If you're using Ubuntu (Gnome) as this forum would suggest you are, then Synaptic should already be installed. If not (say, if you're using KDE), then just open a terminal and type ```
sudo apt-get update
sudo apt-get install synaptic
``` Forget all that .tar.gz, make, make install stuff.

---

### Post by Wheelie on 2005-10-26
[QUOTE=aysiu]If you're using Ubuntu (Gnome) as this forum would suggest you are, then Synaptic should already be installed. If not (say, if you're using KDE), then just open a terminal and type ```
sudo apt-get update
sudo apt-get install synaptic
``` Forget all that .tar.gz, make, make install stuff.[/QUOTE]

Thanks! It is fixed now!

---

