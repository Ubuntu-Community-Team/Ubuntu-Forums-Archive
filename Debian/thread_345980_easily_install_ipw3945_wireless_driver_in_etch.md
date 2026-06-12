---
title: "easily install ipw3945 wireless driver in etch?"
date: 2007-01-25
forum: Debian
---

### Post by rabid emu on 2007-01-25
Ok I tried using etch for a while but didn't like it because it didn't support my wireless card for my laptop.  ubuntu is the only distro I've found to do this so far.  The only solution on other distros is to build the driver from the ipw3945 sourceforge site, and I have never successfully gotten that working.  I know that it works with Ubuntu and Ubuntu is based on Debian.  Is there a moderately easy way to make it work in Debian Etch?  Is there a package in the repos that I just missed?

If I can get my wireless card supported in Debian I may very well use it over Ubuntu since it it supposedly more 'stable' (although ubuntu has never been unstable for me) and it is a more traditional and 'free' GNU/Linux distro.  I want to run Debian, but I also need wireless to work and the method of building it from source and compiling it into the kernel is just way too convoluted for me to get working.

---

### Post by stlutz on 2007-01-27
Debian doesn't ship with a linux-restricted-modules deb like Ubuntu does.  So, for these modules (as with Nvidia cards) you have to build the moduel.  However, it's not that difficult, as they have a little tool called module assistant.  What you need to do is:

a) install the ipw3945 modules and firmware (search for "ipw3945" in synaptic)
b) apt-get install module-assistant
c) module-assistant update
d) module-assistant prepare
e) module-assistant auto-install  ipw3945
f) modprobe ipw3945

Anytime you install a new kernel, you will need to go back through steps c-e.

A great place to check on how people got hardware working on a particular laptop is at [www.linux-laptop.net](www.linux-laptop.net).

---

### Post by patrickfromspain on 2007-01-28
should be easy:

**ipw3945-modules-2.6.18-3-k7**

Intel PRO/Wireless 3945ABG (ipw3945) driver modules for Linux 2.6.18 on AMD K7
This package provides the Intel PRO/Wireless 3945ABG (ipw3945) driver
 modules for the Linux kernel version 2.6.18 on 32bit AMD
Duron/Athlon/AthlonXP machines.

---

### Post by rabid emu on 2007-01-28
Would be nice if I had an AMD processor.

---

### Post by patrickfromspain on 2007-01-30
why don't you replace k7 with 686? It's not that hard ;)

Or better, do a search for ipw3945 in etch...

---

### Post by tturrisi on 2007-01-31
in etch:
apt-get install ipw3945-modules-2.6.18-3-YOUR-KERNEL
[all packages]("http://packages.debian.org/cgi-bin/search_packages.pl?keywords=ipw3945-modules-2.6.18-3&searchon=names&subword=1&version=testing&release=all")

---

### Post by rabid emu on 2007-01-31
Thanks a lot, everyone.

When Etch comes out (next decade *chuckle*) I'll definitely install it and give it a try again.

---

### Post by Mightyspider on 2007-04-22
Hi there im having problems with my drivers aswell im trying to install the drivers bt i get errors all the time this is what i did can anyone help me please?

root@ubuntu-laptop:~# cd Desktop

root@ubuntu-laptop:~/Desktop# ls

Folder  wireless

root@ubuntu-laptop:~/Desktop# cd wireless

root@ubuntu-laptop:~/Desktop/wireless# ls

how to install drivers in linx.txt  ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17                    Merge Wireless Driver.txt
ieee80211-1.2.17.tar.gz             patch-2.6.20.6
ieee80211-1.2.17.tar.gz_FILES       patch-2.6.20.6.bz2
ipw3945-linux-1.2.0                 To login as root.txt
root@ubuntu-laptop:~/Desktop/wireless# cd i
ieee80211-1.2.17/              ipw3945-linux-1.2.0/
ieee80211-1.2.17.tar.gz        ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17.tar.gz_FILES/ 

root@ubuntu-laptop:~/Desktop/wireless# cd i
ieee80211-1.2.17/              ipw3945-linux-1.2.0/
ieee80211-1.2.17.tar.gz        ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17.tar.gz_FILES/ 

root@ubuntu-laptop:~/Desktop/wireless# cd ieee80211-1.2.17

root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# ls

CHANGES                     ieee80211_crypt_tkip.mod.c  ieee80211_module.o.lst
compat.h                    ieee80211_crypt_tkip.mod.o  ieee80211.o
GIT_SHA1                    ieee80211_crypt_tkip.o      ieee80211_rx.c
idvals                      ieee80211_crypt_tkip.o.lst  ieee80211_rx.o
ieee80211_crypt.c           ieee80211_crypt_wep.c       ieee80211_rx.o.lst
ieee80211_crypt_ccmp.c      ieee80211_crypt_wep.ko      ieee80211_tx.c
ieee80211_crypt_ccmp.ko     ieee80211_crypt_wep.mod.c   ieee80211_tx.o
ieee80211_crypt_ccmp.mod.c  ieee80211_crypt_wep.mod.o   ieee80211_tx.o.lst
ieee80211_crypt_ccmp.mod.o  ieee80211_crypt_wep.o       ieee80211_wx.c
ieee80211_crypt_ccmp.o      ieee80211_crypt_wep.o.lst   ieee80211_wx.o
ieee80211_crypt_ccmp.o.lst  ieee80211_geo.c             ieee80211_wx.o.lst
ieee80211_crypt.ko          ieee80211_geo.o             INSTALL
ieee80211_crypt.mod.c       ieee80211_geo.o.lst         in-tree
ieee80211_crypt.mod.o       ieee80211.ko                LICENSE
ieee80211_crypt.o           ieee80211.mod.c             Makefile
ieee80211_crypt.o.lst       ieee80211.mod.o             Modules.symvers
ieee80211_crypt_tkip.c      ieee80211_module.c          net
ieee80211_crypt_tkip.ko     ieee80211_module.o          remove-old
root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.17-10-generic for ieee80211 components...
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.17-10-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.17-10-generic/include/net/ieee80211.h
/lib/modules/2.6.17-10-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.17-10-generic/include/net/ieee80211_radiotap.h
Above files found.  Remove? [y],n y

make -C /lib/modules/2.6.17-10-generic/build M=/root/Desktop/wireless/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:17: 
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:21: 
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'

root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.17-10-generic/build M=/root/Desktop/wireless/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:17: 
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/root/Desktop/wireless/ieee80211-1.2.17/Makefile:21: 
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
install -d /lib/modules/2.6.17-10-generic/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.17-10-generic/net/ieee80211/
install -d `echo /lib/modules/2.6.17-10-generic/include | grep "/net\$" || echo /lib/modules/2.6.17-10-generic/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.17-10-generic/include | grep "/net\$" || echo /lib/modules/2.6.17-10-generic/include/net`
mkdir -p /lib/modules/2.6.17-10-generic/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.17-10-generic/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.17-10-generic

root@ubuntu-laptop:~/Desktop/wireless/ieee80211-1.2.17# cd ..

root@ubuntu-laptop:~/Desktop/wireless# ls

how to install drivers in linx.txt  ipw3945-linux-1.2.0.tgz
ieee80211-1.2.17                    Merge Wireless Driver.txt
ieee80211-1.2.17.tar.gz             patch-2.6.20.6
ieee80211-1.2.17.tar.gz_FILES       patch-2.6.20.6.bz2
ipw3945-linux-1.2.0                 To login as root.txt

root@ubuntu-laptop:~/Desktop/wireless# cd ipw3945-linux-1.2.0

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0# ls

Install_and_Support_Notes.txt  ipw3945d-1.7.22
ipw3945-1.2.0                  ipw3945-ucode-1.14.2

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0# make
make: *** No targets specified and no makefile found.  Stop.

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0# cd ipw3945-1.2.0

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# ls

CHANGES  GIT_SHA1  ipw3945.c         ISSUES       LICENSE.GPL  README.ipw3945
dvals    INSTALL   ipw3945_daemon.h  LICENSE      load         snapshot
FILES    in-tree   ipw3945.h         LICENSE.BSD  Makefile     unload

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# mkae
bash: mkae: command not found

root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# make
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/find_ieee80211: Permission denied
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/check_ieee80211_compat: Permission denied
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0# make install
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/find_ieee80211: Permission denied
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
make: execvp: /root/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0/snapshot/check_ieee80211_compat: Permission denied
install -d /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/
install -m 644 -c ipw3945.ko /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/
install: cannot stat `ipw3945.ko': No such file or directory
make: *** [install] Error 1
root@ubuntu-laptop:~/Desktop/wireless/ipw3945-linux-1.2.0/ipw3945-1.2.0#

---

### Post by Pobega on 2007-04-23
The easiest way to install the firmware/drivers/modules is to enable the non-free and contrib repositories, and install the following packages:

apt-get install firmware-ipw3945 ipw3945-modules-`uname -r` ipw3945d

Then edit /etc/modules, and add a new line with "ipw3945" to the end. Restart and it should work, it's as simple as that!

---

### Post by Mightyspider on 2007-04-23
ok i will try that i dont know how to do it but i will follow the way u said i sould do it because im very new to ubuntu very much he he he 

Thanks

---

### Post by Mightyspider on 2007-04-23
Hi there Pobeg

I try doing the things u told me to do but this is what i get if i do it there is a screenshot attached.

Thanks in advance

---

### Post by Pobega on 2007-04-23
> **Mightyspider said:**
> Hi there Pobeg

I try doing the things u told me to do but this is what i get if i do it there is a screenshot attached.

Thanks in advance

Debian != Ubuntu

You should enable the multiverse and universe repositories (I could be wrong on the names, it's been a while since I've used Ubuntu), run apt-get update and then see what packages have the name ipw3945.

Keep in mind my way is for Debian Etch and later, and doesn't work on Ubuntu at all.

---

