---
title: "synce | module compilation"
date: 2006-08-25
forum: Desktop Environments
---

### Post by lkh on 2006-08-25
Hi,

this is my first post here. And sorry about my English, I'm from Germany. But now my problem:

I want to connect a Windows Mobile 2003 device with my workstation using synce. I installed all packages I was told in a howto. Now the PPC has two USB endpoints and I have to build a new usbserial and ipaq module (for using ttyUSB1).

Therefore I downloaded the kernel-2.6-driver from synce.sourceforge.net. The README told me to change the path to the sources in the Makefile and then to type "make". This I did and got the following message:

```
root@beta:/home/lkh/Downloads/synce/kernel-2.6-driver# make
make: *** Keine Regel vorhanden, um das Target »/usr/src/linux-headers-2.6.15-23-386/drivers/usb/serial/usb-serial.h« 
  benötigt von »usb-serial.h«, zu erstellen.  Schluss.

```
(no rule to make target ... Stop).

This is the Makefile :
```
ifeq ($(KERNELRELEASE),)

#
# Modify the line below if needed
#
LINUX_SOURCE_PATH := /usr/src/linux-headers-$(shell uname -r)
#
# You should not need to modify anything else
#

KERNEL_BUILD_DIR := /lib/modules/$(shell uname -r)/build
USB_SERIAL_SOURCE_DIR := $(LINUX_SOURCE_PATH)/drivers/usb/serial
VERSION = 2.6.13.3
PWD := $(shell pwd)

PATCHED := .patched
FILES := usb-serial.h ipaq.h ipaq.c

default: $(LINUX_SOURCE_PATH) $(USB_SERIAL_SOURCE_DIR) $(FILES) $(PATCHED)
	$(MAKE) -C $(KERNEL_BUILD_DIR) SUBDIRS=$(PWD) modules

all: default

$(LINUX_SOURCE_PATH) $(USB_SERIAL_SOURCE_DIR):
	@echo "Can't find directory $@"
	@echo "Edit $(PWD)/Makefile and provide the correct path to the Linux source tree."
	@false

usb-serial.h: $(USB_SERIAL_SOURCE_DIR)/usb-serial.h
	ln -sf $< $@

ipaq.h: ipaq.h-$(VERSION)
	ln -sf $< $@

ipaq.c: $(PATCHED)
 
$(PATCHED): ipaq.c-$(VERSION)
	cp -p $^ ipaq.c
	patch -N -p0 < ipaq-select-endpoints.diff
	patch -N -p0 < ipaq-version.diff
	patch -N -p4 < ipaq-psion-teklogix.diff
	patch -N -p4 < ipaq-smartphones.diff
	touch $(PATCHED)


install: ipaq.ko
	install -m 644 $< /lib/modules/$(shell uname -r)/kernel/drivers/usb/serial

clean:
	rm -rf $(FILES) $(PATCHED) .tmp_versions *.mod.c *.orig *.o *.ko .*cmd

else
obj-m	:= ipaq.o
endif

```

Now what my system is missing? I have no idea what I need to install.

Thanks for your help ...

---

### Post by lkh on 2006-08-30
No ideas? :confused:

---

