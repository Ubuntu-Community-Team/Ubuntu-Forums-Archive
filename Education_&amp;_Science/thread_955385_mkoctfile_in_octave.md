---
title: "mkoctfile in octave"
date: 2008-10-22
forum: Education &amp; Science
---

### Post by juckou on 2008-10-22
Hello,

I have octave (version 3.0.0) in my computer and I'm trying to install several packages. But whenever I try to install a new package I get the same error realted with mkoctfile:

[COLOR="Blue"]octave:1> pkg install /home/julio/octcdf-1.0.7.tar.gz
configure: WARNING: no mkoctfile found on path
./configure: line 2380: conftest.cc: command not found
configure: error: Could not run 
error: the configure script returned the following error: checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for mkoctfile... no
error: called from `pkg:configure_make' in file /usr/share/octave/3.0.0/m/pkg/pkg.m near line 1045, column 2[/COLOR]

I have checked that mkoctfile is in the octave path (/usr/share/octave/3.0.0/m/miscellaneus/mkoctfile.m) but I'm able to make it work. Maybe it's because I don't have administrator privileges Should I maybe change the place where is octave installed to another where I do have access?

Thank you very much for any help

juckou

---

### Post by juckou on 2008-10-22
I already have it working. Just have to install octave3.0-headers as somebody said before

---

### Post by PC_load_letter on 2009-12-22
Thanks, ur post is a life saver :D

---

### Post by MattPhillips on 2010-02-19
Helped me out too, thanks!

---

### Post by kadeck on 2010-11-05
thanks for the post, great help for me :)

---

### Post by yasirniazkhan on 2010-11-11
Thanks. Helped me as well.

---

### Post by Username4 on 2011-02-02
Thanks. This continues to be helpful.

---

### Post by CarlosDutra on 2011-07-12
Thank you man!

---

### Post by odiss3us on 2012-03-27
Thank you! This helped! (Though for Ubuntu 11.10 it is actually octave3.2-headers.)

---

### Post by papu40000 on 2012-06-12
Thanks!

In my case, I'm in Natty, using the octave 3.6 package in this ppa repository:
[https://launchpad.net/~dr-graef/+archive/octave-3.6](https://launchpad.net/~dr-graef/+archive/octave-3.6)

you could use PPA's for last distro, for example:
[https://launchpad.net/~picaso/+archive/octave](https://launchpad.net/~picaso/+archive/octave)

and I install some packets, but not liboctave-dev, I was thinking, why? I'm not a developer.
But seeing that, seems to be compiling the package of octave-forge. So I installed it and now it works!

remember that with octave-3.6 you could install packages as:
pkg install -forge audio
where audio is a <package>

take a look here
[http://octave.sourceforge.net/packages.php](http://octave.sourceforge.net/packages.php)
and copy&paste the title

---

