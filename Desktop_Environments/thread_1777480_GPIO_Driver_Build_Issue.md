---
title: "GPIO Driver Build Issue"
date: 2011-06-07
forum: Desktop Environments
---

### Post by pauldemet on 2011-06-07
I have a Linux driver for a GPIO card that built fine with version 2.6.32. After upgrading to version 2.6.38 my driver will no longer build. I get the error "pthread.h: No such file or directory". I have verified that this file does in fact exist at /usr/include and that this directory is in the header search path. Don't know why the file is not seen. 
 
The makefile is here:
 
>  
MAJOR = 110
 
EXTRA_CFLAGS += -DMAJOR_NUM=$(MAJOR)
 
ifneq ($(KERNELRELEASE),) # called by kbuild
obj-m := uio48.o
else # called from command line
KERNEL_VERSION = `uname -r`
KERNELDIR := /lib/modules/$(KERNEL_VERSION)/build
PWD := $(shell pwd)
MODULE_INSTALLDIR = /lib/modules/$(KERNEL_VERSION)/kernel/drivers/gpio/
 
default:
$(MAKE) -C $(KERNELDIR) M=$(PWD) modules
 
uio48io.o: uio48io.c uio48.h Makefile
gcc -c $(EXTRA_CFLAGS) uio48io.c
 
all: default install poll flash
 
install:
mkdir -p $(MODULE_INSTALLDIR)
rm -f $(MODULE_INSTALLDIR)uio48.ko
install -c -m 0644 uio48.ko $(MODULE_INSTALLDIR)
/sbin/depmod -a
 
uninstall:
rm -f $(MODULE_INSTALLDIR)uio48.ko
/sbin/depmod -a
 
flash: flash.c uio48.h uio48io.o Makefile
gcc $(EXTRA_CFLAGS) -static flash.c uio48io.o -o flash
chmod a+x flash
 
poll: poll.c uio48.h uio48io.o Makefile
gcc $(EXTRA_CFLAGS) -D_REENTRANT -static poll.c uio48io.o -o poll -lpthread
chmod a+x poll
 
endif
 
 
clean:
rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions /dev/uio48?
 
spotless:
rm -rf ioctl poll flash Module.* *.o *~ core .depend .*.cmd *.ko *.mod.c *.order .tmp_versions /dev/uio48?
 
 
The problem occurs when the default build is attempted.
 
 
Thanks in advance.

---

### Post by pauldemet on 2011-06-08
After further research, it appears that the include file path is different for make and for gcc. When I specifically call out the directory for pthread.h, the include file is seen. I have attempted to specify include directories on the command line with no luck.

---

