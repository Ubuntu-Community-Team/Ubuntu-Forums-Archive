---
title: "ndiswrapper compile error"
date: 2006-10-03
forum: Desktop Environments
---

### Post by mykrob on 2006-10-03
I have a fresh install on a Compaq V5204NR. i am trying to install the newest ndiswrapper. I have installed the kernel source, best i can tell, but i get this error when trying to make ndiswrapper:

```

mykrob@infected-laptop:~/Laptop Docs/ndiswrapper/ndiswrapper-1.24$ make
make -C driver
make[1]: Entering directory `/home/mykrob/Laptop Docs/ndiswrapper/ndiswrapper-1.24/driver'
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/mykrob/Laptop Docs/ndiswrapper/ndiswrapper-1.24/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
make[2]: *** No rule to make target `Docs/ndiswrapper/ndiswrapper-1.24/driver'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mykrob/Laptop Docs/ndiswrapper/ndiswrapper-1.24/driver'
make: *** [all] Error 2

```

what am i missing? what do i need to do?

thanks,
-myk

---

### Post by az on 2006-10-03
*** No rule to make target `Docs/ndiswrapper/ndiswrapper-1.24/driver'.  Stop.


That should be "Laptop Docs".  Unix does not handle directory names with spaces in them very well.

Why recompile ndiswrapper?  Just use the version that comes on the disk.  There are very very few devices that require you use the very latest version.

You do need to have the latest version of the .inf file.  The one that came with your card may be too old.

---

### Post by mykrob on 2006-10-03
thank you. I was running mepis on the laptop,and the driver wouldnt work with the stock ndiswrapper, but worked fine with the newest compiled version.. Trying the same with ubuntu.

---

