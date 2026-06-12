---
title: "Why Does ./configure Never Work?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Mark76 on 2006-10-07
I'm trying to install the gaim-rhythmbox plugin but all I ever get is 

> ./configure
bash: ./configure: No such file or directory


---

### Post by Old Pink on 2006-10-07
After doing:
tar xzf thisistheinstallfile.tar.gz

You must do:
cd thisistheinstallfile

Before attempting ./configure :)

---

### Post by someguyouknow on 2006-10-07
also, make sure you check out the readME file to make sure you are doing it right...

---

### Post by NESFreak on 2006-10-07
is there a configure file? check out the readme

NESFreak

---

### Post by Old Pink on 2006-10-07
> **NESFreak said:**
> is there a configure file? check out the readme

He's right, for example with [Flock]("http://matt.moved.in/?p=18") it was ./flock :)

---

### Post by Mark76 on 2006-10-07
Why the hell is the terminal not recognising the "make" command?

I have it pointed to the right bleeding directory.

---

### Post by Mark76 on 2006-10-07
tar xvf /home//gaim-rhythmbox-1.5.0.1.tar.gz
gaim-rhythmbox-1.5.0.1/
gaim-rhythmbox-1.5.0.1/src/
gaim-rhythmbox-1.5.0.1/src/aim.h
gaim-rhythmbox-1.5.0.1/src/rb-proxy.c
gaim-rhythmbox-1.5.0.1/src/rb-proxy.h
gaim-rhythmbox-1.5.0.1/src/aim_cbtypes.h
gaim-rhythmbox-1.5.0.1/src/Makefile.am
gaim-rhythmbox-1.5.0.1/src/Makefile.in
gaim-rhythmbox-1.5.0.1/src/faimconfig.h
gaim-rhythmbox-1.5.0.1/src/aim_internal.h
gaim-rhythmbox-1.5.0.1/src/gaim-rhythmbox.c
gaim-rhythmbox-1.5.0.1/NEWS
gaim-rhythmbox-1.5.0.1/TODO
gaim-rhythmbox-1.5.0.1/depcomp
gaim-rhythmbox-1.5.0.1/aclocal.m4
gaim-rhythmbox-1.5.0.1/README
gaim-rhythmbox-1.5.0.1/ltmain.sh
gaim-rhythmbox-1.5.0.1/configure
gaim-rhythmbox-1.5.0.1/configure.ac
gaim-rhythmbox-1.5.0.1/config.guess
gaim-rhythmbox-1.5.0.1/install-sh
gaim-rhythmbox-1.5.0.1/config.sub
gaim-rhythmbox-1.5.0.1/missing
gaim-rhythmbox-1.5.0.1/Makefile.am
gaim-rhythmbox-1.5.0.1/Makefile.in
gaim-rhythmbox-1.5.0.1/AUTHORS
gaim-rhythmbox-1.5.0.1/INSTALL
gaim-rhythmbox-1.5.0.1/ChangeLog
gaim-rhythmbox-1.5.0.1/COPYING
 cd /home//gaim-rhythmbox-1.5.0.1.tar.gz
bash: cd: /home//gaim-rhythmbox-1.5.0.1.tar.gz: Not a directory
 cd /home/mark-williams/gaim-rhythmbox-1.5.0.1
~/gaim-rhythmbox-1.5.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
~/gaim-rhythmbox-1.5.0.1$ make
bash: make: command not found
:~/gaim-rhythmbox-1.5.0.1$ sudo make install
Password:
sudo: make: command not found
~/gaim-rhythmbox-1.5.0.1$ make /home/mark-williams/gaim-rhythmbox-1.5.0.1
bash: make: command not found
~/gaim-rhythmbox-1.5.0.1$

---

### Post by tht00 on 2006-10-07
Looks like you need the compilers.  Install the 'build-essential' package through synaptic or run 'sudo apt-get install build-essential'.

---

