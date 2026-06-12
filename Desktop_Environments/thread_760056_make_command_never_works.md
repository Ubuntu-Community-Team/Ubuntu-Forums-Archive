---
title: "make command never works"
date: 2008-04-19
forum: Desktop Environments
---

### Post by brendan6 on 2008-04-19
I've seen a few topics come up about the make command to work but always seem to be answered with "Search for the package on the repositories" or something similar. Unfortunately that won't work in this situation as the version i need is not in the repositories.

Terminal:
brendan@brendan-desktop:~/Downloads/libusb-1_0_devel$ ls
acconfig.h      COMPILE.CVS    COPYING            install-sh        NEWS
aclocal.m4      config.h.in    CVS                libusb-config.in  README.in
AUTHORS         config.log     depcomp            libusb.spec.in    src
autogen.sh      config.status  doc                LICENSE           tests
autom4te.cache  configure      examples           Makefile.am       TODO.linux
ChangeLog       configure.in   INSTALL.libusb.in  missing
brendan@brendan-desktop:~/Downloads/libusb-1_0_devel$ ./configure
#<-------REMOVED TO SAVE SPACE (NO ERRORS)------------------->
brendan@brendan-desktop:~/Downloads/libusb-1_0_devel$ make
make: *** No targets specified and no makefile found.  Stop.
brendan@brendan-desktop:~/Downloads/libusb-1_0_devel$ 

Well what about Makefile.am? Why doesnt it recognize this? And what do i do to finish the install?

What i really don't understand is package specific installing instructions tell me i can simply do:
./configure; make
But i ALWAYS get this type of error...

---

### Post by mike2357 on 2008-04-19
I would re-run configure but re-direct the output to a file (./configure > OUT_CONFIGURE).  When it is finished, check the output and make sure there isn't some sort of error.  Then I would check to see if there is a configure.log or some other log file as it may show an error.  I suspect that configure isn't completing properly, and therefore a makefile (or Makefile) isn't being created.

As to your question about why "make" isn't reading Makefile.am, unless you specify parameters, "make" will use makefiles with names of GNUmakefile, makefile or Makefile.  You can use a -f option and specify a different makefile name.  You can read more with the command "man make".  So "make -f Makefile.am" will cause make to compile code with that file.  However, I don't recommend it, because I suspect something caused the "configure" step to stop prematurely and not create a file with the name "Makefile".

---

### Post by russo.mic on 2008-04-20
Make sure you have build-essentials package installed.  That is your kernel sources to compile against.

sudo apt-get install build-essentials

Russo

---

### Post by FredB on 2008-04-21
make and other build tools are indeed available with build-essential meta-package.

---

