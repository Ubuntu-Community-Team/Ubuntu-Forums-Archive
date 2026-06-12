---
title: "trying to install .tar file but &quot;make&quot; giving errors"
date: 2009-04-14
forum: General Help
---

### Post by bobhope on 2009-04-14
I'm trying to install TARP from this website
[http://siis.cse.psu.edu/tools.html](http://siis.cse.psu.edu/tools.html)

When i type make I get these errors

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-eeepc'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/nick/Downloads/tarp/module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/nick/Downloads/tarp/module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-eeepc'
make: *** [default] Error 2

This is the makefile they are referring to

INSTALL = install

KVER    := $(shell uname -r)
ARP_PACKET_TYPE_ADDR :=$(shell grep -w arp_packet_type /boot/System.map-$(KVER) | awk {'print "0x"$$1'})
CFLAGS += -DARP_PACKET_TYPE_ADDR=$(ARP_PACKET_TYPE_ADDR)

ifneq ($(KERNELRELEASE),)
obj-m    := tarp_mod.o

else
KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
endif


install:
    $(INSTALL) -d /lib/modules/`uname -r`/kernel/net/ipv4
    $(INSTALL) -m 744 tarp_mod.ko /lib/modules/`uname -r`/kernel/net/ipv4

clean:
    rm *.o *.ko *~

How the hell do I fix it to use extra flags?

---

### Post by bobhope on 2009-04-15
nobody knows how to fix this?

---

### Post by ibuclaw on 2009-04-15
In the /home/nick/Downloads/tarp/module/Makefile, change line 5:
```
CFLAGS += -DARP_PACKET_TYPE_ADDR=$(ARP_PACKET_TYPE_ADDR)
```
to
```
EXTRA_CFLAGS += -DARP_PACKET_TYPE_ADDR=$(ARP_PACKET_TYPE_ADDR)
```


Also, make sure you have all build-deps ;)
```
sudo apt-get install libpcap-dev libnet1-dev libssl-dev openssl iproute-dev
```

Regards
Iain

---

### Post by InvisibleMan on 2009-06-10
This is very similar to my problem (Jaunty server, trying to install driver for on-board Intel NIC). 


A brief summary:
Fresh load of Jaunty server, not fully connecting to network to pick up MAC-based static DHCP lease. Unloaded e100 module to install new driver from Intel. 

First error: Makefile:65. Linux-source not found
Solution: Install linux-headers

Second error: Makefile:122 Compiler not found
Solution: Install build-essential

Latest error: Makefile.build:46 CFLAGS was changed.
Solution: ???


My Makefile has about 10 references to CFLAGS. Which one do I need to change? All of them?


I'm surprised how challenging it is for this distribution to pick up a reasonably common network card.

---

