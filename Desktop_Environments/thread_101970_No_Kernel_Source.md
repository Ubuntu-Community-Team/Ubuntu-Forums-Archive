---
title: "No Kernel Source?"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Airjoe on 2005-12-11
Hi.
I'm a pretty much a linux newb, and I'm trying to get my linksys wireless PCI card to work. 

I downloaded ndiswrapper.
I did 
make distclean
sudo -s
(Inputted password)
make

At "make", I get a errors
"make -C driver
make[1]: Entering directory '/home/myname/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/myname/ndiswrapper-1.7/driver'
make: *** [all] error 2"

At the ndiswrapper install page, it says I have to do 
"ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build"

but /usr/src is completely empty.
What do I have to do? Thanks!

---

### Post by mo_x on 2005-12-11
sudo apt-get install linux-headers-2.6.12.-9-386

---

### Post by mo_x on 2005-12-11
I think the ndiswrapper module is provided by Ubunto so you don't have to compile it yourself.
sudo modprobe ndiswrapper

---

