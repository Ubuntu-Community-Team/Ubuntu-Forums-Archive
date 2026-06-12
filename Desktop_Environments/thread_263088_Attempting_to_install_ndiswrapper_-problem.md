---
title: "Attempting to install ndiswrapper -problem"
date: 2006-09-22
forum: Desktop Environments
---

### Post by puppy on 2006-09-22
Hi folks, I have downloaded and unzipped ndiswrapper, and moved into the ndiswrapper folder, but when I type "make" I get the following output -

make -C driver
make[1]: Entering directory `/home/pete/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.17-8-generic/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/pete/ndiswrapper-1.23/driver'
make: *** [all] Error 2

What do I now? I need to get on with installing my wireless card :sad:

---

### Post by Nonno Bassotto on 2006-09-22
Did you try the version in the repositories first? If you can connect with a cable open Synaptic (under System->Administration) and install ndisgtk and ndiswrapper-utils. Otherwise download these packages from [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndis&searchon=names&subword=1&version=dapper&release=all") on another computer, then move the two files on your pc and double click them.

---

### Post by puppy on 2006-09-22
Just reinstalled all the applications and I get exactly the same error :(

---

### Post by puppy on 2006-09-23
Any advice? Do I need to copy packages anywhere??

---

### Post by rain4ever on 2008-03-03
i have run into the exact same problem. i had figured it out once before but i just recently had to reinstall ubuntu and i am just blank right now, cant seem to remember...

---

