---
title: "network-manager purgatory, tales of ndiswrapper pain"
date: 2007-06-14
forum: Dell  Ubuntu Support
---

### Post by doobey on 2007-06-14
I'm a newbie doing something for me quite complex. I have several questions, in bold. Please be patient with me. It took me a while to get this far and I feel I almost got it!!!!

I am following these directions (in case it matters) to install driver for my wireless broadcom bcm4318 (dell insprion 1300)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5BAirForce_One_54g%5D)
these directions involve replacing network manager with wicd also

**1) does the two "x"s in this command really mean "x", or do I put in the numbers corresponding to my card ?** I know this is a dumb Q, but it seemed to work with verbatim. 
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

**2) if, in order to fix #3) below, i must get ubuntu back on-line, how can I undo these commands without reinstalling** I'm using another computer to get on-line.
sudo apt-get remove network-manager network-manager-gnome
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9

**3) can you tell me why this command failed, and what to do about it?** The file was properly unpacked and in the directory specified.

daved@daved-laptop:~/ndis/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/daved/ndis/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/daved/ndis/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/daved/ndis/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/daved/ndis/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/daved/ndis/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/daved/ndis/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/daved/ndis/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: Leaving directory `/home/daved/ndis/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/daved/ndis/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â€˜size_tâ€™
loadndisdriver.c: In function â€˜load_fileâ€™:
loadndisdriver.c:67: error: â€˜size_tâ€™ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â€˜;â€™ before â€˜sizeâ€™
loadndisdriver.c:68: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:71: warning: implicit declaration of function â€˜basenameâ€™
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function â€˜openâ€™
loadndisdriver.c:73: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â€˜syslogâ€™
loadndisdriver.c:75: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:75: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â€˜strerrorâ€™
loadndisdriver.c:75: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:76: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function â€˜fstatâ€™
loadndisdriver.c:81: warning: implicit declaration of function â€˜closeâ€™
loadndisdriver.c:84: error: â€˜sizeâ€™ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function â€˜mmapâ€™
loadndisdriver.c:86: error: â€˜PROT_READâ€™ undeclared (first use in this function)
loadndisdriver.c:86: error: â€˜MAP_PRIVATEâ€™ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: â€˜MAP_FAILEDâ€™ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function â€˜strncpyâ€™
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:95: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:96: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:69: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜parse_setting_lineâ€™:
loadndisdriver.c:109: warning: implicit declaration of function â€˜isspaceâ€™
loadndisdriver.c:115: warning: implicit declaration of function â€˜strchrâ€™
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function â€˜strchrâ€™
loadndisdriver.c:115: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:117: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:117: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:118: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function â€˜strlenâ€™
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
loadndisdriver.c: In function â€˜read_conf_fileâ€™:
loadndisdriver.c:150: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:151: error: â€˜FILEâ€™ undeclared (first use in this function)
loadndisdriver.c:151: error: â€˜configâ€™ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function â€˜lstatâ€™
loadndisdriver.c:158: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:158: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:158: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:160: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function â€˜sscanfâ€™
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function â€˜sscanfâ€™
loadndisdriver.c:178: warning: implicit declaration of function â€˜fopenâ€™
loadndisdriver.c:178: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function â€˜fgetsâ€™
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:205: warning: implicit declaration of function â€˜fcloseâ€™
loadndisdriver.c:150: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜load_bin_fileâ€™:
loadndisdriver.c:217: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:217: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function â€˜tolowerâ€™
loadndisdriver.c:221: warning: implicit declaration of function â€˜chdirâ€™
loadndisdriver.c:222: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:224: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:232: warning: implicit declaration of function â€˜ioctlâ€™
loadndisdriver.c:232: warning: implicit declaration of function â€˜_IOWâ€™
loadndisdriver.c:232: error: expected expression before â€˜structâ€™
loadndisdriver.c: In function â€˜load_driverâ€™:
loadndisdriver.c:249: error: â€˜DIRâ€™ undeclared (first use in this function)
loadndisdriver.c:249: error: â€˜driver_dirâ€™ undeclared (first use in this function)
loadndisdriver.c:251: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:255: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:255: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:257: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:259: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function â€˜opendirâ€™
loadndisdriver.c:267: warning: implicit declaration of function â€˜mallocâ€™
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function â€˜mallocâ€™
loadndisdriver.c:271: warning: implicit declaration of function â€˜memsetâ€™
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:280: warning: implicit declaration of function â€˜readdirâ€™
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function â€˜statâ€™
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function â€˜S_ISREGâ€™
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function â€˜strcasecmpâ€™
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function â€˜strcpyâ€™
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function â€˜strcpyâ€™
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:318: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable â€˜statbufâ€™
loadndisdriver.c:344: error: expected expression before â€˜structâ€™
loadndisdriver.c:346: warning: implicit declaration of function â€˜closedirâ€™
loadndisdriver.c:348: warning: implicit declaration of function â€˜freeâ€™
loadndisdriver.c:355: warning: implicit declaration of function â€˜munmapâ€™
loadndisdriver.c:355: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:355: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c:357: error: â€˜struct load_driver_fileâ€™ has no member named â€˜dataâ€™
loadndisdriver.c:357: error: â€˜struct load_driver_fileâ€™ has no member named â€˜sizeâ€™
loadndisdriver.c: In function â€˜get_deviceâ€™:
loadndisdriver.c:367: error: storage size of â€˜statbufâ€™ isnâ€™t known
loadndisdriver.c:370: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:370: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:373: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:374: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function â€˜snprintfâ€™
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function â€˜strncpyâ€™
loadndisdriver.c:367: warning: unused variable â€˜statbufâ€™
loadndisdriver.c: In function â€˜load_deviceâ€™:
loadndisdriver.c:419: error: â€˜DIRâ€™ undeclared (first use in this function)
loadndisdriver.c:419: error: â€˜dirâ€™ undeclared (first use in this function)
loadndisdriver.c:423: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:423: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function â€˜memsetâ€™
loadndisdriver.c:426: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:427: error: â€˜EINVALâ€™ undeclared (first use in this function)
loadndisdriver.c:429: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before â€˜structâ€™
loadndisdriver.c: In function â€˜get_ioctl_deviceâ€™:
loadndisdriver.c:464: error: â€˜FILEâ€™ undeclared (first use in this function)
loadndisdriver.c:464: error: â€˜proc_miscâ€™ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function â€˜strstrâ€™
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function â€˜strstrâ€™
loadndisdriver.c:473: warning: implicit declaration of function â€˜strtolâ€™
loadndisdriver.c:473: error: â€˜NULLâ€™ undeclared (first use in this function)
loadndisdriver.c:483: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:483: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function â€˜unlinkâ€™
loadndisdriver.c:489: warning: implicit declaration of function â€˜mknodâ€™
loadndisdriver.c:489: error: â€˜S_IFCHRâ€™ undeclared (first use in this function)
loadndisdriver.c:489: error: â€˜MISC_MAJORâ€™ undeclared (first use in this function)
loadndisdriver.c:490: error: â€˜errnoâ€™ undeclared (first use in this function)
loadndisdriver.c:495: error: â€˜O_RDONLYâ€™ undeclared (first use in this function)
loadndisdriver.c: In function â€˜mainâ€™:
loadndisdriver.c:511: warning: implicit declaration of function â€˜openlogâ€™
loadndisdriver.c:511: error: â€˜LOG_PERRORâ€™ undeclared (first use in this function)
loadndisdriver.c:511: error: â€˜LOG_CONSâ€™ undeclared (first use in this function)
loadndisdriver.c:511: error: â€˜LOG_KERNâ€™ undeclared (first use in this function)
loadndisdriver.c:511: error: â€˜LOG_DEBUGâ€™ undeclared (first use in this function)
loadndisdriver.c:513: error: â€˜LOG_INFOâ€™ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function â€˜strncmpâ€™
loadndisdriver.c:517: warning: implicit declaration of function â€˜printfâ€™
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function â€˜printfâ€™
loadndisdriver.c:527: warning: implicit declaration of function â€˜atoiâ€™
loadndisdriver.c:542: warning: implicit declaration of function â€˜atofâ€™
loadndisdriver.c:549: warning: implicit declaration of function â€˜strcmpâ€™
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function â€˜sscanfâ€™
loadndisdriver.c:590: warning: implicit declaration of function â€˜closelogâ€™
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/daved/ndis/ndiswrapper-1.47/utils'
make: *** [all] Error 2
daved@daved-laptop:~/ndis/ndiswrapper-1.47$

---

### Post by neptho on 2007-06-15
> **doobey said:**
> **1) does the two "x"s in this command really mean "x", or do I put in the numbers corresponding to my card ?** I know this is a dumb Q, but it seemed to work with verbatim. 
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

Yes, it  does mean 'xx.'

> **2) if, in order to fix #3) below, i must get ubuntu back on-line, how can I undo these commands without reinstalling** I'm using another computer to get on-line.
sudo apt-get remove network-manager network-manager-gnome
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9

You can't 'un-remove' a program; you have to reinstall it.  You'll need to connect to wired ethernet and:

```
grep -v 'bcm43xx' /etc/modprobe.d/blacklist >> /tmp/blacklist
mv /tmp/blacklist /etc/modprobe.d/blacklist
apt-get --reinstall install network-manager network-manager-gnome ndiswrapper-common ndis-wrapper-utils-1.9
```

> **3) can you tell me why this command failed, and what to do about it?** The file was properly unpacked and in the directory specified.

Most of your headers are missing.  When you're connected via wired ethernet, you need to:
```
apt-get install build-essential linux-heders-generic
```

Good luck!

---

