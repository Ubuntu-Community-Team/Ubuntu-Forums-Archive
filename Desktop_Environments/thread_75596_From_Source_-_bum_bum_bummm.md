---
title: "From Source - bum bum bummm"
date: 2005-10-13
forum: Desktop Environments
---

### Post by LinkRJH on 2005-10-13
I got the gstreamer from source because the apt-get wasn't working and when I get to ./configure it breaks.  Why is this?

linkrjh@gigahertzog:~/gstreamer-0.9.3$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
configure: configuring gstreamer for release
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
linkrjh@gigahertzog:~/gstreamer-0.9.3$

---

### Post by aysiu on 2005-10-13
Have you tried doing ```
sudo apt-get install build-essential
``` first?

---

### Post by DeathOnJuice on 2005-10-13
Try sudo apt-get install gcc. That might not be the exact package name, but I think that will install the stable release of gcc. After that, compile the plugins.

---

### Post by LinkRJH on 2005-10-13
Thank you very much for the quick responces.

Here is what happens when I try those things...

linkrjh@gigahertzog:~/gstreamer-0.9.3$ apt-get install build-essential
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
linkrjh@gigahertzog:~/gstreamer-0.9.3$ apt-get install gcc
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
linkrjh@gigahertzog:~/gstreamer-0.9.3$

---

### Post by drogoh on 2005-10-13
Typically when somebody says something about 'apt-get', using 'sudo' before that command is implied too and in fact most everybody prepends 'sudo', as above.

---

### Post by LinkRJH on 2005-10-13
linkrjh@gigahertzog:~/gstreamer-0.9.3$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
                   Depends: make but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  kmuddy: Depends: kdelibs4 (>= 4:3.4.1-1) but it is not installable
          Depends: libidn11 (>= 0.5.18) but 0.5.13-1.0 is to be installed
          Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
          Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not going to be installed
          Depends: libsvga1 but it is not installable
          Depends: libxrender1 (> 1:0.9.0-1) but 1:0.9.0-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
linkrjh@gigahertzog:~/gstreamer-0.9.3$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gcc: Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
  kmuddy: Depends: kdelibs4 (>= 4:3.4.1-1) but it is not installable
          Depends: libidn11 (>= 0.5.18) but 0.5.13-1.0 is to be installed
          Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable
          Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not going to be installed
          Depends: libsvga1 but it is not installable
          Depends: libxrender1 (> 1:0.9.0-1) but 1:0.9.0-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
linkrjh@gigahertzog:~/gstreamer-0.9.3$

---

### Post by LinkRJH on 2005-10-13
Seriously thank you for the quick responses and help...this kind of stuff is very discouraging me.

---

### Post by BLTicklemonster on 2005-10-13
Hang in there Link! You'll be mastering all this before long. And it will be worth it!

---

### Post by SickTwist on 2005-10-14
try this:

sudo apt-get -f install

apt-get will try to fix the problem (probably by offering to uninstall some things). Do not worry if it wants to remove many things. After that is done, use this command to re-install the standard Ubuntu desktop:

sudo apt-get install ubuntu-base

---

