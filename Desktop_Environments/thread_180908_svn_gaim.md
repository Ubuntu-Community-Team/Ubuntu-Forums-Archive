---
title: "svn gaim"
date: 2006-05-23
forum: Desktop Environments
---

### Post by ELD on 2006-05-23
Hi all currently trying to get the latest svn from gaim, came with these errors:
> 
liam@ubuntu:~$ cd gaim
liam@ubuntu:~/gaim$ ./autogen.sh
Generating configuration files for Gaim, please wait....

Running libtoolize, please ignore non-fatal messages....
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
You should add the contents of '/usr/share/aclocal/intltool.m4' to 'aclocal.m4'.aclocal: configure.ac: 50: macro `AM_GLIB_GNU_GETTEXT' not found in library
liam@ubuntu:~/gaim$


What do i need to do to get past these errors?

Many thanks!

---

### Post by joshuapurcell on 2006-05-25
Are these errors that stopped you from proceeding? The first line below the blank line says the ignore non-fatal messages. What instructions are you following? These instructions seem to work well for me... I believe they are the same instructions I followed to get gaim2.0 installed on my system:
[https://wiki.ubuntu.com/CompileGaim](https://wiki.ubuntu.com/CompileGaim)

---

### Post by ELD on 2006-05-25
I got it, the actual 'gmake' wasn't installed...lol

---

