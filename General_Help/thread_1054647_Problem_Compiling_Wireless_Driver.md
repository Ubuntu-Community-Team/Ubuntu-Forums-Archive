---
title: "Problem Compiling Wireless Driver"
date: 2009-01-29
forum: General Help
---

### Post by errantknave on 2009-01-29
I've been trying to compile [this wireless driver.]("http://www.encore-usa.com/download/driver/ENLWI-N_ENPWI-N_Linux_Driver.zip")  This is the output that I get:

make -C tools

make[1]: Entering directory `/home/wes/WirelessDriv/tools'

gcc -g bin2h.c -o bin2h

make[1]: Leaving directory `/home/wes/WirelessDriv/tools'

/home/wes/WirelessDriv/tools/bin2h

cp -f os/linux/Makefile.6 os/linux/Makefile

make V=1  -C  /lib/modules/2.6.27-7-generic/build SUBDIRS=/os/linux modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'

test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\

	echo;								\

	echo "  ERROR: Kernel configuration is invalid.";		\

	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\

	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\

	echo;								\

	/bin/false)

mkdir -p /os/linux/.tmp_versions ; rm -f /os/linux/.tmp_versions/*

make -f scripts/Makefile.build obj=/os/linux

make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

make[2]: *** No rule to make target `/os/linux/../../common/md5.o', needed by `/os/linux/rt2860sta.o'.  Stop.

make[1]: *** [_module_/os/linux] Error 2

make: *** [LINUX] Error 2


Any help would be appreciated.

---

### Post by rwstoner on 2009-01-29
The errors you are getting indicates that is having some issues compiling the code based off the kernel headers and source you currently have.  A lot of time to compile drivers and things of that nature the compiler has to reference specific things regarding your kernel.

The first step would be to run in a terminal
**sudo apt-get install linux-headers-$(uname -r)**

and also run if you haven't yet
**sudo apt-get install build-essential**

After that I would try to recompile the code again.  You may have to do a 'make clean' before attempting to compile since the first attempt failed.

---

### Post by errantknave on 2009-01-29
I ran both of the commands, and both were said to be the newest version.  I also tried the 'make clean' before attempting to make again, but got the same result.

---

