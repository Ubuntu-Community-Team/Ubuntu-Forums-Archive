---
title: "Ndiswrapper troubles"
date: 2006-08-18
forum: Desktop Environments
---

### Post by joshier on 2006-08-18
Fresh install of ubuntu 6.06.

Installed essentials from disc using synaptic.

Used ndiswrapper for my bcm 4318

ndiswrapper doesn't work.

Uninstalled ndiswrapper and ndiswrapper tools to update.

Downloaded ndiswrapper 1.2.3

Upon going into Terminal, typing su, and doing 'make distclean' the following error comes up:

> 
root@exs-laptop:/home/exs/Desktop/UBUNTU# cd ndiswrapper-1.23
root@exs-laptop:/home/exs/Desktop/UBUNTU/ndiswrapper-1.23# make distclean
make -C driver clean
make[1]: Entering directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/driver'
make -C utils clean
make[1]: Entering directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/utils'
rm -f *~
rm -fr ndiswrapper-1.23 ndiswrapper-1.23.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: Leaving directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/driver'
make -C utils distclean
make[1]: Entering directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/utils'
rm -f .\#*
root@exs-laptop:/home/exs/Desktop/UBUNTU/ndiswrapper-1.23# make
make -C driver
make[1]: Entering directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-23-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/exs/Desktop/UBUNTU/ndiswrapper-1.23/driver'
make: *** [all] Error 2


---

### Post by joshier on 2006-08-18
Please Help! or if not, I'll stick with mepis.

---

### Post by jimmymac on 2006-08-18
Have you tried the HowTo [here]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm43xx")

HTH

Jimmy

---

### Post by joshier on 2006-08-18
> **jimmymac said:**
> Have you tried the HowTo [here]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm43xx")

HTH

Jimmy

Brilliant, it's working :) :) (typing from ubuntu)

---

