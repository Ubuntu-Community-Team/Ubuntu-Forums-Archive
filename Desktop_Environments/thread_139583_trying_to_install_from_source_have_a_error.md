---
title: "trying to install from source have a error"
date: 2006-03-04
forum: Desktop Environments
---

### Post by tidy_boy on 2006-03-04
hey guys I am trying to install amsn from source.

I have downloaded it extracted it cd in to the directory and I get this.

How do i sort this?

root@ubuntu:/home/matt/Desktop/amsn-0.95# ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH



Thanks

---

### Post by localzuk on 2006-03-04
You need to install build-essential from the repositories.

---

### Post by tidy_boy on 2006-03-04
thanks I have just installed that and I did the ./configure and got this 

root@ubuntu:/home/matt/Desktop/amsn-0.95# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

---

### Post by Spano on 2006-03-04
```
sudo apt-get install tcl8.4 tcl8.4-dev
```

Look inside your amsn file for a README there may be other packages you need to install before you can compile.

---

### Post by tidy_boy on 2006-03-04
still get the error even installing what you said


root@ubuntu:/home/matt/Desktop/amsn-0.95# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

---

### Post by tidy_boy on 2006-03-04
this is the readme file


This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

========================================================
=== Alvaro's Messenger==================================
CCMSN was great but unfortunately its original author
abandoned the project. Although it was very functional it
still needed major work to improve its look and feel
as well as complete the protocol support among many
other things. That's when we, originally two working on
it separately, decided to join efforts and bring to you
this fine (we hope) piece of work ;)

Alvaro J. Iradier
D. Emilio Grimaldo T.

Please send bugs, comments, feedback or suggestions to
Source Forge project page at:
[http://sourceforge.net/projects/amsn](http://sourceforge.net/projects/amsn)

New versions, and homepage at:
[http://amsn.sourceforge.net](http://amsn.sourceforge.net)

---

### Post by Spano on 2006-03-04
Let me read the amsn web page and get back to you.  Have you tried Gaim - its availible in the repositories and works well with msn messenger?

---

### Post by tidy_boy on 2006-03-04
yeah I use gaim now but prefer the latest amsn :D

Thanks

---

### Post by tidy_boy on 2006-03-04
anyone else got any ideas?


Thanks

---

### Post by localzuk on 2006-03-04
I would advise taking a look at this page:
[http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions](http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions)
It provides a list of required software dependencies and advice how to get past errors such as those seen by yourself.

---

### Post by taurus on 2006-03-04
But there is a binary version for Debian and Debian (Sarge), [http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.deb](http://prdownloads.sourceforge.net/amsn/amsn_0.95-3.deb), so why not use "dpkg -i" to install it!!!  :rolleyes:

---

### Post by localzuk on 2006-03-04
Ubuntu is not binary compatible any more is it though? So this might ask for dependencies that aren't there...

---

### Post by Spano on 2006-03-04
OK in your amsn file re-read the file called "Install"  says you need tcl-dev and tk-dev packages b4 you can install.  The Ubuntu equivilent is plplot-tcl-dev so
```
sudo apt-get install plplot-tcl-dev
```

I would go into synaptic and un-install that other stuff I suggested.

I also see at the website there is a i386.deb package for this program.  You could try that - you will still need plplot-tcl-dev installed.

---

### Post by tidy_boy on 2006-03-04
Sorted it now thanks for your help mate

---

### Post by Spano on 2006-03-04
your welcome

---

