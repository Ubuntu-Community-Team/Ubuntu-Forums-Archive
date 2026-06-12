---
title: "problems installing ndiswrapper/ missing /lib/modules/build"
date: 2005-12-10
forum: General Help
---

### Post by ren wins on 2005-12-10
i'm trying to get ndiswrapper installed so i can possibly have functioning wireless internet
i USED to have kinda spoty wifi
but this is my 3rd reinstall, and i havent been able to get the wireless internet to work at all yet

when trying to compile ndiswrapper, i get these errors

> laserwolf@violet:~/ndiswrapper-1.7$ sudo make uninstall
Password:
make: Warning: File `version' has modification time 1.2e+08 s in the future
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper': Is a directory
removing /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
make: warning:  Clock skew detected.  Your build may be incomplete.

laserwolf@violet:~/ndiswrapper-1.7$ sudo make
make: Warning: File `version' has modification time 1.2e+08 s in the future
make -C driver
make[1]: Entering directory `/home/laserwolf/ndiswrapper-1.7/driver'
make[1]: Warning: File `../version' has modification time 1.2e+08 s in the future
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/laserwolf/ndiswrapper-1.7/driver'
make: *** [all] Error 2

laserwolf@violet:~/ndiswrapper-1.7$ sudo make install
make: Warning: File `version' has modification time 1.2e+08 s in the future
make -C driver install
make[1]: Entering directory `/home/laserwolf/ndiswrapper-1.7/driver'
make[1]: Warning: File `../version' has modification time 1.2e+08 s in the future
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/laserwolf/ndiswrapper-1.7/driver'
make: *** [install] Error 2


according to the install.txt file in ndiswrapper, i'm supposed to have a folder called /lib/modules/2.6.12-9-386/build, which as far as i can tell, i dont have (as you can see in the errors). i think i'm supposed to have a specific file in that folder, but the install.txt is on my ubuntu/windows desktop, which is currently on a time-out

i really hope you guys can help
b/c ubuntu seems like a great OS
but if i cant get wifi to work, i dont have internet on it
and if i dont have internet on it... i cant really do anything with it

thanks in advance

---

### Post by ren wins on 2005-12-10
the only folders in /lib/modules/2.6.12-9-386 are ./initrd ./kernel ./madwifi and ./volatile

according to the ndiswrapper install file, it's supposed to have ./build with "at least 'include' directory and a '.config' file

---

### Post by teaker1s on 2005-12-10
make sure you have 'build-essential' installed before trying to compile then
./configure

check for any missing dependencies and resolve them and if there are none 
make
sudo make install
or install 'checkinstall' with synaptic

and 

make
sudo check install

---

### Post by ren wins on 2005-12-10
./configure?
what?

i installed the build-essentials
i couldnt find checkinstall in synaptic
which isnt supprising, considering that i have no internet access on my linux machine, and therefore dont have any repositories installed

---

### Post by ren wins on 2005-12-10
i dont know what you wanted me to do w/ ./configure (or where to find it)

but after installing build-essentials, i still got errors
```
laserwolf@violet:~/ndiswrapper-1.7$ sudo make uninstall
Password:
make: Warning: File `version' has modification time 1.2e+08 s in the future
NOTE: Not all installed files are removed, as different distributions install nd iswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear bel ow.
removing /lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper ': Is a directory
make: *** [uninstall] Error 1

laserwolf@violet:~/ndiswrapper-1.7$ sudo make
make: Warning: File `version' has modification time 1.2e+08 s in the future
make -C driver
make[1]: Entering directory `/home/laserwolf/ndiswrapper-1.7/driver'
make[1]: Warning: File `../version' has modification time 1.2e+08 s in the futur e
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/laserwolf/ndiswrapper-1.7/driver'
make: *** [all] Error 2

laserwolf@violet:~/ndiswrapper-1.7$ make install
make: Warning: File `version' has modification time 1.2e+08 s in the future
make -C driver install
make[1]: Entering directory `/home/laserwolf/ndiswrapper-1.7/driver'
make[1]: Warning: File `../version' has modification time 1.2e+08 s in the futur e
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/laserwolf/ndiswrapper-1.7/driver'
make: *** [install] Error 2

```

---

### Post by ren wins on 2005-12-10
where do i find my kernel sources?

---

### Post by ren wins on 2005-12-10
i also dont know how to check for dependancy issues, but there doesnt seem to be any

---

### Post by az on 2005-12-10
The ndiswrapper that comes with the distro is perfecty fine.  You do not need to recompile it.

the module is already in your kernel.  You can load it with

sudo modprobe ndiswrapper


the userspace tools are in the ndiswrapper-utils package on the cd.

sudo apt-get install ndiswrapper-utils 
(or use synaptic and yourother favorite package manager)

You need to have the most recent .inf file.  The one that came with the device may be too old for ndiswrapper.  The development of ndiswrapper uses only the most recent drivers - that is usually the problem.

So, if you really really want to recompile ndiswrapper (or any other kernel module)

sudo apt-get install build-essential linux-headers-2.6.12-(whatever your kernel is) gcc-3.4

and that provides the /build link you mentioned in your first post.

---

### Post by ren wins on 2005-12-13
ok, i got the driver to install (2.0.0.2 or something)
but sudo modprobe ndiswrapper returns the error
"FATAL: ndiswrapper module could not be found"
near as i can tell, the rest of it installed ok

i still dont have internet access tho. iwconfig says i'm not getting a signal from the router, which shouldnt be true, because it worked well enough a few weeks ago
and it worked perfectly a few months ago (tho in windows)
:(
i suppose it's time i bring these problems to the networking forums

---

