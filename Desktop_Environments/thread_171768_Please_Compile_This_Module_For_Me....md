---
title: "Please Compile This Module For Me..."
date: 2006-05-07
forum: Desktop Environments
---

### Post by hellmet on 2006-05-07
Hello people..
I am havin some tuff time trying to compile this thing.
I need Linux_source for this..which I don't have.
its a 35 MB file..that'll take ages to download for me.



[B]I am Presently on Breezy Badger(Kernel 2.6x)
I need you guys to Compile the Kernal Module for me
There is the make file that must be edited acc. to your kernel
Please do it..I beg of u guys...[/B]

---

### Post by joft on 2006-05-07
Hi,

I don't think, that the driver source you posted is intended to be compiled using Linux kernel series 2.6.x .... It's for 2.4.x only. And, in fact I tried and got a lot of error messages ...
The readme says something about 8139C+ support, so you have such a chip, right? AFAIK the kernel already has such a driver (8139cp.ko => sudo modprobe 8139cp). Are you sure, that the one provided with the breezy standard kernel does not work?
What do the logs say (or dmesg)?

---

### Post by towsonu2003 on 2006-05-07
first things first, you need these
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

```
you might also need gcc-3.4. Both of the above (but not gcc-3.4, who knows why) are supposed to be in the Install CD thru apt-get. 

Anyway, after changing a line in Makefile to link to the linux-headers, I tried compiling it and got errors, pasted here for OP or anyone who might wanna give it a try: 
```

~$ CC=gcc-3.4 make
gcc -O6 -Wall -DCONFIG_KERNELD -DMODULE -D__KERNEL__ -DLINUX  -I /usr/src/linux/include/ -c 8139too.c
In file included from /usr/src/linux/include/asm/processor.h:18,
                 from /usr/src/linux/include/asm/thread_info.h:17,
                 from /usr/src/linux/include/linux/thread_info.h:21,
                 from /usr/src/linux/include/linux/spinlock.h:12,
                 from /usr/src/linux/include/linux/capability.h:45,
                 from /usr/src/linux/include/linux/sched.h:7,
                 from /usr/src/linux/include/linux/module.h:10,
                 from 8139too.c:107:
/usr/src/linux/include/asm/system.h: In function &#8216;__set_64bit_var&#8217;:
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
/usr/src/linux/include/asm/system.h:193: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /usr/src/linux/include/linux/irq.h:21,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/skbuff.h:27,
                 from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/asm/irq.h:16:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/skbuff.h:27,
                 from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/linux/irq.h: At top level:
/usr/src/linux/include/linux/irq.h:72: error: &#8216;NR_IRQS&#8217; undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/irq.h:74,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/skbuff.h:27,
                 from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/asm/hw_irq.h:28: error: &#8216;NR_IRQ_VECTORS&#8217; undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/if_ether.h:107,
                 from /usr/src/linux/include/linux/netdevice.h:29,
                 from 8139too.c:112:
/usr/src/linux/include/linux/skbuff.h: In function &#8216;skb_add_data&#8217;:
/usr/src/linux/include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of &#8216;csum_and_copy_from_user&#8217; differ in signedness
8139too.c: In function &#8216;rtl8139_init_board&#8217;:
8139too.c:813: warning: implicit declaration of function &#8216;init_etherdev&#8217;
8139too.c:813: warning: assignment makes pointer from integer without a cast
8139too.c:931: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
8139too.c:932: error: &#8216;struct pci_dev&#8217; has no member named &#8216;slot_name&#8217;
8139too.c: In function &#8216;rtl8139_init_one&#8217;:
8139too.c:1053: error: &#8216;struct pci_dev&#8217; has no member named &#8216;driver_data&#8217;
8139too.c: In function &#8216;rtl8139_remove_one&#8217;:
8139too.c:1136: error: &#8216;struct pci_dev&#8217; has no member named &#8216;driver_data&#8217;
8139too.c:1164: error: &#8216;struct pci_dev&#8217; has no member named &#8216;driver_data&#8217;
8139too.c: In function &#8216;rtl8139_open&#8217;:
8139too.c:1382: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
8139too.c: In function &#8216;rtl8139CP_open&#8217;:
8139too.c:1570: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
8139too.c: In function &#8216;rtl8139_thread&#8217;:
8139too.c:1926: error: too few arguments to function &#8216;daemonize&#8217;
8139too.c:1927: error: &#8216;struct task_struct&#8217; has no member named &#8216;sigmask_lock&#8217;
8139too.c:1929: error: too many arguments to function &#8216;recalc_sigpending&#8217;
8139too.c:1930: error: &#8216;struct task_struct&#8217; has no member named &#8216;sigmask_lock&#8217;
8139too.c: In function &#8216;rtl8139_set_rx_mode&#8217;:
8139too.c:2994: warning: passing argument 2 of &#8216;set_bit&#8217; from incompatible pointer type
8139too.c: In function &#8216;rtl8139_suspend&#8217;:
8139too.c:3019: error: &#8216;struct pci_dev&#8217; has no member named &#8216;driver_data&#8217;
8139too.c: In function &#8216;rtl8139_resume&#8217;:
8139too.c:3051: error: &#8216;struct pci_dev&#8217; has no member named &#8216;driver_data&#8217;
make: *** [8139too.o] Error 1

```

I have no idea whether the errors are bc this is for 2.4 kernel.

---

