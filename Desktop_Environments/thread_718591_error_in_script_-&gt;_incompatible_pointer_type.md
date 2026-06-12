---
title: "error in script? -&gt; incompatible pointer type"
date: 2008-03-08
forum: Desktop Environments
---

### Post by WernerBrandt on 2008-03-08
Hij all!

Could someone please point me in the right direction / help me with this install script?

I am installing the Dlink / Devolo homeplug devices. Downloaded the driver and config files.
But now I am getting an 'incompatible pointer type' script error

I did following:

```
 ./configure 
```

No errors, only wierd thing was:

```
checking for local pcap library... not found
```

But I thought it wasn 't something very important.

Then I issued a ' make' command and got following error:

```
make
making all in tool
make[1]: Entering directory `/home/w/powerline/dLAN-linux-package-v4/tool'
gcc -O2 -Wall    -DHAVE_CONFIG_H  -DSON_PROCESS_NAME=\"/usr/local/sbin/dlanconfig_son\" -DDLANSOFTWARE_VERSION=\"v4\" -DSNIFFING_CHILD_PROCESS=\"dlanconfig_son\"  -M sha256.c md5.c dlanconfig.c dlanconfig_son.c > .depend
gcc -O2 -Wall    -DHAVE_CONFIG_H  -DSON_PROCESS_NAME=\"/usr/local/sbin/dlanconfig_son\" -DDLANSOFTWARE_VERSION=\"v4\" -DSNIFFING_CHILD_PROCESS=\"dlanconfig_son\"    -c -o dlanconfig_son.o dlanconfig_son.c
gcc dlanconfig_son.o -lpcap   -o dlanconfig_son
gcc -O2 -Wall    -DHAVE_CONFIG_H  -DSON_PROCESS_NAME=\"/usr/local/sbin/dlanconfig_son\" -DDLANSOFTWARE_VERSION=\"v4\" -DSNIFFING_CHILD_PROCESS=\"dlanconfig_son\"    -c -o dlanconfig.o dlanconfig.c
dlanconfig.c: In function ‘IfOldVersion’:
dlanconfig.c:754: warning: pointer targets in passing argument 1 of ‘strstr’ differ in signedness
gcc -O2 -Wall    -DHAVE_CONFIG_H  -DSON_PROCESS_NAME=\"/usr/local/sbin/dlanconfig_son\" -DDLANSOFTWARE_VERSION=\"v4\" -DSNIFFING_CHILD_PROCESS=\"dlanconfig_son\"    -c -o md5.o md5.c
gcc -O2 -Wall    -DHAVE_CONFIG_H  -DSON_PROCESS_NAME=\"/usr/local/sbin/dlanconfig_son\" -DDLANSOFTWARE_VERSION=\"v4\" -DSNIFFING_CHILD_PROCESS=\"dlanconfig_son\"    -c -o sha256.o sha256.c
gcc   dlanconfig.o md5.o sha256.o   -o dlanconfig
make[1]: Leaving directory `/home/w/powerline/dLAN-linux-package-v4/tool'
making all in driver
make[1]: Entering directory `/home/w/powerline/dLAN-linux-package-v4/driver'
./kerneldir.sh /lib/modules/2.6.22-14-generic/build
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.o
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c:22:26: error: linux/config.h: No such file or directory
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c: In function ‘devolo_read_bulk_callback’:
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c:153: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c: In function ‘devolo_start_xmit’:
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c:249: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c: In function ‘devolo_open’:
/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.c:358: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
make[3]: *** [/home/w/powerline/dLAN-linux-package-v4/driver/devolo_usb.o] Error 1
make[2]: *** [_module_/home/w/powerline/dLAN-linux-package-v4/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/w/powerline/dLAN-linux-package-v4/driver'
make: *** [all] Error 2

```

I think the script is looking for a file (config.h) but cannot find it, correct?


Ok, what to do now?

NOTE:
1. Attached is the install package
2. below is the code of the makefile script, I think the error is around line 34
3. I am running Kubuntu Gutsy

makefile script :
```

##################################################
SHELL=/bin/bash
CC= gcc
LN_S=ln -s
VERSION=v4
DEFS=-DHAVE_CONFIG_H -DVERSION=$(VERSION)

module_prefix=/lib/modules
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe
INSTALL=/usr/bin/install -c
INSTALL_PROGRAM=${INSTALL}
INSTALL_DATA=${INSTALL} -m 644

KERNELDIR=/lib/modules/2.6.22-14-generic/build

MKDIR=mkdir -p
USBDEF=-DUSBMGR=\"uhci\"
DESTDIR=


INSTALLDIR=$(DESTDIR)/lib/modules/2.6.22-14-generic/kernel/drivers/net
INSTALLDIR26=$(DESTDIR)/lib/modules/2.6.22-14-generic/extra

MODVERSION_INCLUDE=

kern26=y

DRIVER=devolo_usb
BOOTPROG=devolo
INSTALLWARNFILE=INSTALL
BOOTDIR=/etc/init.d

obj-m:=$(DRIVER).o

MODFIL=/etc/modprobe.conf

TARGET=$(DRIVER).o

.PHONY: clean distclean install uninstall installdriver installboot uninstallboot

ifeq ("$(kern26)","y")
all: default
CFLAGS +=$(USBDEF)	

installdriver: 
	$(MKDIR) $(INSTALLDIR26) && $(INSTALL_DATA) $(DRIVER).ko $(INSTALLDIR26)
#	$(MAKE) -C $(KERNELDIR) SUBDIRS=$(PWD) modules_install 

uninstalltarget:
	rm -f $(INSTALLDIR26)/$(DRIVER).ko && $(DEPMOD) -a
#	$(MAKE) -C $(KERNELDIR) SUBDIRS=$(PWD) modules_uninstall 

default:
	./kerneldir.sh $(KERNELDIR) 

else


CFLAGS= -Wall -Werror -Wstrict-prototypes -Wno-trigraphs -O2 -Wall -I$(KERNELDIR)/include -D__KERNEL__ -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-boundary=2 -march=i686 -DMODULE  -DKBUILD_BASENAME=devolo_usb $(MODVERSION_INCLUDE) $(USBDEF)	

all: $(TARGET)

installdriver: $(TARGET) 
	$(MKDIR) $(INSTALLDIR) && \
	$(INSTALL_DATA) $(TARGET) $(INSTALLDIR) 

uninstalltarget:  
	rm -f $(INSTALLDIR)/$(TARGET)

$(TARGET): $(DRIVER).c $(DRIVER).h

endif

######################################################


install: insdriver modulesconf message 

uninstall: uninstalltarget uninstallboot

insdriver: installdriver
	$(DEPMOD) -a &&	$(MODPROBE) $(DRIVER)

# alias string in /etc/modules.conf
modulesconf:
	@if test -f $(MODFIL); then \
	   for i in 0 1 2 3 ; do \
		STR="alias dlanusb$$i devolo_usb" ;\
		grep "$$STR" $(MODFIL) || echo "$$STR" >> $(MODFIL);\
	   done; \
         fi

message:
	@echo ; \
	echo "In order to have your usb driver running and configured"; \
	echo "at boot, you should go into driver directory and type"; \
	echo; \
	echo "    make installboot";\
	echo


installboot: $(BOOTPROG)
	@./installboot.sh

uninstallboot:
	@./installboot.sh uninstall

clean:
	rm -f  *~ core $(DRIVER).o $(DRIVER).ko $(DRIVER).mod.* 

distclean:
	rm Makefile 



```

---

### Post by walmartshopper67 on 2008-03-09
After a quick look (moving back to RIT day, ugh), it looks to me like you're missing libpcap. It's in the repositories - install that and try again, and post the results, and we'll go from there. 

Good luck;)

---

### Post by WernerBrandt on 2008-03-10
Hi, thanx for the reply.

But no, that cannot be the case, because I do have libpcap, 08 and the  08-dev. version

---

### Post by WernerBrandt on 2008-03-11
bump..

Anyone?

---

