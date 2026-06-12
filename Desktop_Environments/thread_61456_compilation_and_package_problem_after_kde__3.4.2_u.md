---
title: "compilation and package problem after kde  3.4.2 upgrade"
date: 2005-08-31
forum: Desktop Environments
---

### Post by vanaedium on 2005-08-31
Hi
I have a problem with compilation:
when i compiled amarok 1.3 during the configure appeared this error

configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev.

then I tried to reconfigure amarok 1.3 beta 3 that I have already installed with compilation and checkinstall but with my surprise the same error during configure!!!

I searched the package libstdc++-dev in synaptic but always permission denied!!! what is permission denied? I run synaptic as root for sure. I have also tried to install gcc 4.0 but this is the output error:

E: /var/cache/apt/archives/gcc-4.0_4.0-0pre6ubuntu7_i386.deb:  impossible to create the directory `./usr/share/doc/gcc-4.0-base/gcc': Input/output error.

this is very strange because my kubuntu was perfect and now this mysterious problem. I have tried to install different package and SOMETIMES everything is ok.
i've also tried to upgrade kde to 3.4.2: all ok eccepts one package called kdesdk-scripts:

E: /var/cache/apt/archives/kdesdk-scripts_4-0x1.5e7820000006bp-1363.4.2-0ubuntu0hoary2_all.deb:  impossible to run stat() su `./usr/lib/valgrind/kde.supp' : Permission denied

thank  to all for help me

---

### Post by incinerator on 2005-09-01
You don't want to use gcc-4.0 with hoary, use 3.3 or 3.4. I would simply install the build-essential package and go on from there.

Several possible reasons here:

1.) Some odd library conflicts or maybe you have deinstalled some important packages necessary for installation.
2.) do a g++ --version
3.) Is your hard disk mounted read-write?
4.) Does your hard disk have space left or is it almost filled up?

---

### Post by gnutux on 2005-09-01
Install the required library stated by the package.

apt-get it.

gnutux

---

