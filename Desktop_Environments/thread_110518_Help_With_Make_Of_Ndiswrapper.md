---
title: "Help With Make Of Ndiswrapper"
date: 2005-12-31
forum: Desktop Environments
---

### Post by Psycho_Penguin on 2005-12-31
I'm a newbie to Ubuntu and Linux in general and I'm trying to get my netgear WG311 v3 wireless card working and I downloaded and un-tar.gz-ed Ndiswrapper and installed build-essential but when I try make it says: 
> <my username>@ubuntu:~/Desktop/ndiswrapper-1.7$ make
make -C driver
make[1]:entering directory `/home/<my username>/Desktop/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/<my username>/Desktop/ndiswrapper-1.7/driver'
make: *** [all] Error 2

Please tell me how to get this to work. I've almost given up on this and am about ready to switch back to an OS that has available drivers.

---

### Post by art on 2005-12-31
You need to install kernel headers, do a search in synaptics for "headers" and install the one which matches your kernel, which you can find from doing 

uname -r 

in command line

---

### Post by Lambert on 2005-12-31
Here's a howto on installing latest ndiswrapper.
[http://www.ubuntuforums.org/showthread.php?t=104539](http://www.ubuntuforums.org/showthread.php?t=104539)

You also need to install gcc-3.4

---

### Post by Psycho_Penguin on 2005-12-31
Thanks for replying so fast. I like the HowTo and I installed the kernel headers but when I try to install gcc-3.4 it gives me this error:
> <my username>@ubuntu:...$ sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
Reading package lists... Done
Building dependancy tree... Done
Package dh-make is not available, but it is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package dh-make has no installation canadate

What am I missing now? Please help me I am so frusterated.

---

### Post by az on 2005-12-31
Have you tried it with the version of ndiswrapper that ships with ubuntu?  All you need to do is install ndiswrapper-utils (which is on the cd and cached on your harddrive).

If you have the very most recent windows drier (INF file) it should work.  You should not need to recompile ndiswrapper from source.

---

### Post by spasticteapot on 2006-01-01
I have a similar problem with dh-make. I'm a total newbie to Linux; however, I know that there are no packages called dh-make in synaptic, and that I apparently need to download it.
Also, NDISwrapper does not support some Belkin drivers, like the ones I need to use.  I imagine that the OP has similar issues.

---

### Post by az on 2006-01-01
Try this windows driver for the WG311 v3 card

[http://www.marvell.com/drivers/driverDisplay.do?dId=122&pId=3](http://www.marvell.com/drivers/driverDisplay.do?dId=122&pId=3)

It is reported to work.  (Using the stock ubuntu ndiswrapper)

See this page for where to get the most up-to-date inf files.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

As for the Belkin drivers, same thing.  Get the most latest broadcom (or realtek, if that is your chipset) and you *should* not have a problem.

---

### Post by deadlycow21 on 2006-06-27
This may be different with a AMD chipset, netgear has released some things indicating that it does not work on AMD chipsets (it runs for awhile in windows then crashs), but i will try those drivers.

anyone know the exact chipset it runs on? something like marvell 8000 or something

---

