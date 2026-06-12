---
title: "problem while compiling the file"
date: 2008-12-04
forum: General Help
---

### Post by shariefbe on 2008-12-04
Hello...i am trying to compile the USBCORE module seperately...for that i tried to compile with the make seperately from desktop....but i am getting so many errors...i dont in which place its making error.....i will post the errors and makefile below..can anyone tell me what to do..

make -C /lib/modules/2.6.22.14/build M=/home/sharief/Desktop/drivers/core modules
make[1]: Entering directory `/usr/src/linux-2.6.22.14'
CC [M] /home/sharief/Desktop/drivers/core/usb.o
/home/sharief/Desktop/drivers/core/usb.c:20:19: error: errno.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:21:19: error: fcntl.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:22:20: error: unistd.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:23:19: error: stdio.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:24:20: error: memory.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:25:21: error: pthread.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:26:20: error: signal.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:27:20: error: stdlib.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:29:23: error: sys/types.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:30:22: error: sys/stat.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:31:23: error: sys/ioctl.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:32:22: error: sys/poll.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:37:32: error: linux/usb/gadgetfs.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:45:23: error: usbstring.h: No such file or directory
/home/sharief/Desktop/drivers/core/usb.c:212: error: array type has incomplete element type
/home/sharief/Desktop/drivers/core/usb.c:220: error: variable &#8216;strings&#8217; has initializer but incomplete type
/home/sharief/Desktop/drivers/core/usb.c:221: error: unknown field &#8216;language&#8217; specified in initializer
/home/sharief/Desktop/drivers/core/usb.c:221: warning: excess elements in struct initializer
/home/sharief/Desktop/drivers/core/usb.c:221: warning: (near initialization for &#8216;strings&#8217;)
/home/sharief/Desktop/drivers/core/usb.c:222: error: unknown field &#8216;strings&#8217; specified in initializer
/home/sharief/Desktop/drivers/core/usb.c:222: warning: excess elements in struct initializer
/home/sharief/Desktop/drivers/core/usb.c:222: warning: (near initialization for &#8216;strings&#8217;)
/home/sharief/Desktop/drivers/core/usb.c:248: warning: function declaration isn&#8217;t a prototype
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;autoconfig&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:249: error: storage size of &#8216;statb&#8217; isn&#8217;t known
/home/sharief/Desktop/drivers/core/usb.c:252: warning: implicit declaration of function &#8216;stat&#8217;
/home/sharief/Desktop/drivers/core/usb.c:427: error: &#8216;ENODEV&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:427: error: (Each undeclared identifier is reported only once
/home/sharief/Desktop/drivers/core/usb.c:427: error: for each function it appears in.)
/home/sharief/Desktop/drivers/core/usb.c:249: warning: unused variable &#8216;statb&#8217;
/home/sharief/Desktop/drivers/core/usb.c: At top level:
/home/sharief/Desktop/drivers/core/usb.c:685: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ep0&#8217;
/home/sharief/Desktop/drivers/core/usb.c:687: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;source&#8217;
/home/sharief/Desktop/drivers/core/usb.c:690: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;sink&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;close_fd&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:703: warning: implicit declaration of function &#8216;pthread_self&#8217;
/home/sharief/Desktop/drivers/core/usb.c:703: error: &#8216;ep0&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:704: warning: implicit declaration of function &#8216;ioctl&#8217;
/home/sharief/Desktop/drivers/core/usb.c:704: error: &#8216;GADGETFS_FIFO_STATUS&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:707: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:707: error: &#8216;ENODEV&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:707: error: &#8216;EOPNOTSUPP&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:708: warning: implicit declaration of function &#8216;perror&#8217;
/home/sharief/Desktop/drivers/core/usb.c:710: warning: implicit declaration of function &#8216;fprintf&#8217;
/home/sharief/Desktop/drivers/core/usb.c:710: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:713: error: &#8216;GADGETFS_FIFO_FLUSH&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:720: warning: implicit declaration of function &#8216;close&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;ep_config&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:738: warning: implicit declaration of function &#8216;open&#8217;
/home/sharief/Desktop/drivers/core/usb.c:738: error: &#8216;O_RDWR&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:740: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:741: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:742: warning: implicit declaration of function &#8216;strerror&#8217;
/home/sharief/Desktop/drivers/core/usb.c:748: warning: implicit declaration of function &#8216;memcpy&#8217;
/home/sharief/Desktop/drivers/core/usb.c:752: warning: implicit declaration of function &#8216;write&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;fill_in_buf&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:793: warning: implicit declaration of function &#8216;memset&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;empty_out_buf&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:833: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;simple_source_thread&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:861: warning: implicit declaration of function &#8216;pthread_cleanup_push&#8217;
/home/sharief/Desktop/drivers/core/usb.c:868: warning: implicit declaration of function &#8216;pthread_testcancel&#8217;
/home/sharief/Desktop/drivers/core/usb.c:879: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:880: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:880: error: &#8216;ESHUTDOWN&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:882: warning: implicit declaration of function &#8216;fflush&#8217;
/home/sharief/Desktop/drivers/core/usb.c:882: error: &#8216;stdout&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:884: warning: implicit declaration of function &#8216;pthread_cleanup_pop&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;simple_sink_thread&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:907: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:908: warning: implicit declaration of function &#8216;read&#8217;
/home/sharief/Desktop/drivers/core/usb.c:916: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:917: error: &#8216;ESHUTDOWN&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:919: error: &#8216;stdout&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c: At top level:
/home/sharief/Desktop/drivers/core/usb.c:1187: warning: function declaration isn&#8217;t a prototype
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;start_io&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1188: error: &#8216;sigset_t&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1188: error: expected &#8216;;&#8217; before &#8216;allsig&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1213: warning: implicit declaration of function &#8216;sigfillset&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1213: error: &#8216;allsig&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1214: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1214: warning: implicit declaration of function &#8216;pthread_sigmask&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1214: error: &#8216;SIG_SETMASK&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1214: error: &#8216;oldsig&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1225: warning: implicit declaration of function &#8216;pthread_create&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1225: error: &#8216;source&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1231: error: &#8216;sink&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1234: warning: implicit declaration of function &#8216;pthread_cancel&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1235: error: &#8216;ep0&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1244: warning: implicit declaration of function &#8216;sched_yield&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1250: warning: implicit declaration of function &#8216;exit&#8217;
/home/sharief/Desktop/drivers/core/usb.c: At top level:
/home/sharief/Desktop/drivers/core/usb.c:1255: warning: function declaration isn&#8217;t a prototype
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;stop_io&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1256: warning: implicit declaration of function &#8216;pthread_equal&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1256: error: &#8216;source&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1256: error: &#8216;ep0&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1258: warning: implicit declaration of function &#8216;pthread_join&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1263: error: &#8216;sink&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;init_device&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1307: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1312: error: &#8216;O_RDWR&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1315: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1339: error: &#8216;EIO&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;handle_control&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1355: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1376: error: invalid use of undefined type &#8216;struct usb_gadget_strings&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1378: warning: implicit declaration of function &#8216;usb_gadget_get_string&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1386: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1386: error: &#8216;EIDRM&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1461: error: &#8216;GADGETFS_CLEAR_HALT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1498: error: &#8216;EL2HLT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c: At top level:
/home/sharief/Desktop/drivers/core/usb.c:1502: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;siginfo_t&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;signothing&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1506: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;ep0_thread&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1529: error: storage size of &#8216;action&#8217; isn&#8217;t known
/home/sharief/Desktop/drivers/core/usb.c:1531: error: storage size of &#8216;ep0_poll&#8217; isn&#8217;t known
/home/sharief/Desktop/drivers/core/usb.c:1533: error: &#8216;source&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1533: error: &#8216;sink&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1533: error: &#8216;ep0&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1541: error: &#8216;SA_SIGINFO&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1542: warning: implicit declaration of function &#8216;sigaction&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1542: error: &#8216;SIGINT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1546: error: &#8216;SIGQUIT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1552: error: &#8216;POLLIN&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1552: error: &#8216;POLLOUT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1552: error: &#8216;POLLHUP&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1558: error: array type has incomplete element type
/home/sharief/Desktop/drivers/core/usb.c:1568: warning: implicit declaration of function &#8216;poll&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1570: warning: implicit declaration of function &#8216;time&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1575: warning: implicit declaration of function &#8216;ctime_r&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1576: warning: implicit declaration of function &#8216;printf&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1587: error: &#8216;errno&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1587: error: &#8216;EAGAIN&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1588: warning: implicit declaration of function &#8216;sleep&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1596: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1601: error: &#8216;GADGETFS_NOP&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1605: error: &#8216;GADGETFS_CONNECT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1613: error: &#8216;GADGETFS_SETUP&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1617: error: &#8216;GADGETFS_DISCONNECT&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1624: error: &#8216;GADGETFS_SUSPEND&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1637: error: &#8216;stdout&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1558: warning: unused variable &#8216;event&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1531: warning: unused variable &#8216;ep0_poll&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1529: warning: unused variable &#8216;action&#8217;
/home/sharief/Desktop/drivers/core/usb.c: In function &#8216;main&#8217;:
/home/sharief/Desktop/drivers/core/usb.c:1658: warning: implicit declaration of function &#8216;srand&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1660: warning: implicit declaration of function &#8216;rand&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1668: warning: implicit declaration of function &#8216;getopt&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1668: error: &#8216;EOF&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1700: warning: implicit declaration of function &#8216;atoi&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1700: error: &#8216;optarg&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1703: warning: implicit declaration of function &#8216;strncpy&#8217;
/home/sharief/Desktop/drivers/core/usb.c:1709: error: &#8216;stderr&#8217; undeclared (first use in this function)
/home/sharief/Desktop/drivers/core/usb.c:1717: warning: implicit declaration of function &#8216;chdir&#8217;
make[2]: *** [/home/sharief/Desktop/drivers/core/usb.o] Error 1
make[1]: *** [_module_/home/sharief/Desktop/drivers/core] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22.14'
make: *** [all] Error 2

**_MAKEFILE_**

root@sharief-desktop:/home/sharief/Desktop/drivers/core# cat Makefile
#
# Makefile for USB Core files and filesystem
#

usbcore-objs := usb.o hub.o hcd.o urb.o message.o driver.o \
config.o file.o buffer.o sysfs.o endpoint.o \
devio.o notify.o generic.o quirks.o

ifeq ($(CONFIG_PCI),y)
usbcore-objs += hcd-pci.o
endif

ifeq ($(CONFIG_USB_DEVICEFS),y)
usbcore-objs += inode.o devices.o
endif

obj-$(CONFIG_USB) += usbcore.o

ifeq ($(CONFIG_USB_DEBUG),y)
EXTRA_CFLAGS += -DDEBUG
endif

all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

---

### Post by shariefbe on 2008-12-04
i am Using Ubuntu 7.10...kernel version 2.6.22.14....please tell me what to do?

---

### Post by shariefbe on 2008-12-04
sorry i changed the kernel...old shows error while booting...but here i am getting diffenet warnings..
After changing the version...Now i am getting different errors and warnings...
sharief@sharief-desktop:~/Desktop/linux2/sub/core$ make
make -C /lib/modules/2.6.20/build M=/home/sharief/Desktop/linux2/sub/core modules
make[1]: Entering directory `/home/sharief/Desktop/linux2/linux-2.6.20'
Building modules, stage 2.
MODPOST 0 modules
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100036) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100044) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:init_pg_tables_end from .text between '_text' (at offset 0xc01000a6) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .text between 'is386' (at offset 0xc0100221) and 'check_x87'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_prepare_cpus from .text between 'init' (at offset 0xc0100437) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:migration_init from .text between 'init' (at offset 0xc010043c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_ksoftirqd from .text between 'init' (at offset 0xc0100441) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_softlockup_task from .text between 'init' (at offset 0xc0100446) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_cpus_done from .text between 'init' (at offset 0xc01004c2) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sched_init_smp from .text between 'init' (at offset 0xc01004c7) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpuset_init_smp from .text between 'init' (at offset 0xc01004cc) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:usermodehelper_init from .text between 'init' (at offset 0xc01004d6) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:driver_init from .text between 'init' (at offset 0xc01004db) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysctl_init from .text between 'init' (at offset 0xc01004e1) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc0100503) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc010051c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.textrepare_namespace from .text between 'init' (at offset 0xc01006ff) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem from .text between 'init_gdt' (at offset 0xc010a05b) and 'cpu_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem from .text between 'init_gdt' (at offset 0xc010a071) and 'cpu_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysenter_setup from .text between 'identify_cpu' (at offset 0xc010a6cb) and 'display_cacheinfo'
WARNING: vmlinux - Section mismatch: reference to .init.text:mtrr_bp_init from .text between 'identify_cpu' (at offset 0xc010a6d5) and 'display_cacheinfo'
WARNING: vmlinux - Section mismatch: reference to .init.text:trap_init_f00f_bug from .text between 'init_intel' (at offset 0xc010c726) and 'cpuid4_cache_lookup'
WARNING: vmlinux - Section mismatch: reference to .init.data:initkmem_list3 from .text between 'set_up_list3s' (at offset 0xc01706df) and 's_start'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'pci_eisa_init' (at offset 0xc0260c6b) and 'virtual_eisa_release'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'virtual_eisa_root_init' (at offset 0xc0260ccf) and 'cpufreq_unregister_driver'
WARNING: vmlinux - Section mismatch: reference to .init.text: from .text between 'iret_exc' (at offset 0xc02e43f0) and '_etext'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .paravirtprobe between '__start_paravirtprobe' (at offset 0xc03adcf0) and '__stop_paravirtprobe'
make[1]: Leaving directory `/home/sharief/Desktop/linux2/linux-2.6.20'
sharief@sharief-desktop:~/Desktop/linux2/sub/core

---

### Post by shariefbe on 2008-12-05
its only warning but i didnt get any .ko file that is any module file...dont know what to do....anyone help me..

---

