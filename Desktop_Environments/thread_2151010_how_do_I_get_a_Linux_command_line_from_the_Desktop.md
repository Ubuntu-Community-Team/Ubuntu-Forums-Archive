---
title: "how do I get a Linux command line from the Desktop GUI"
date: 2013-06-03
forum: Desktop Environments
---

### Post by scicom on 2013-06-03
Brand New to Ubuntu and Linux

I need to install a .tar for a program called Open SRF. The installation instructions state that I need to issue commands as the "root user" to install prerequisites using the Makefile.install prerequisite installer. 

the commands are 

apt-get install make 
make -f src/extras/makefile.install <ubuntu-precise>

How do I get from the GUI to a command line so that I can go from the "user" environment to the "root" so that I can type these commands in and be able to install the OpenSRF tarball?

In brief: I think I need to have a Linux command line, but am not sure where to get one fired up from the Ubuntu desktop GUI. Is this a "command Line install", Cli - I think this is related to a command called 'sudotaskel"


THANKS
AJ

---

### Post by PureTryOut on 2013-06-03
In Ubuntu, press Ctrl + Alt + T (T from Terminal), and the console (terminal) will pop-up.
Now type "sudo -s", you can now type every command using root without typing "sudo" before every command.

---

### Post by ajgreeny on 2013-06-03
You may need to install build-essentials package before you can compile, configure and install anything, so it's worth getting that first, just in case it is needed for this.

---

### Post by Lars Noodén on 2013-06-03
Also, it's usually possible to do the *./configure* and *make* as a non-root user.  Only *make install* should require root access.  It is tidier that way.  You may also want to look into rolling your own .deb package for that application.  If there are any dependencies, that should help with them.  It will also make it easier to uninstall if you no longer need the package around any more.

---

