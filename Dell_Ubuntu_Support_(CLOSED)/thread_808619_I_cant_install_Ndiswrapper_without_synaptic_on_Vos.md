---
title: "I cant install Ndiswrapper without synaptic on Vostro 1400"
date: 2008-05-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rrsn on 2008-05-26
I'm try install Ndiswrapper without synaptic. 
I tried follow this document but don't worked >> [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")

I receive this message:
ndiswrapper: command not found

run make install:
```

make -C driver install
make[1]: Entering directory `/home/roberto/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.24-16-generic SUBDIRS=/home/roberto/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
echo /lib/modules/2.6.24-16-generic/misc
/lib/modules/2.6.24-16-generic/misc
mkdir -p /lib/modules/2.6.24-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.24-16-generic/misc
/sbin/depmod -a 2.6.24-16-generic -b /
make[1]: Leaving directory `/home/roberto/ndiswrapper-1.52/driver'
make -C utils install
make[1]: Entering directory `/home/roberto/ndiswrapper-1.52/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before â&#128;&#152;size_tâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;load_fileâ&#128;&#153;:
loadndisdriver.c:67: error: â&#128;&#152;size_tâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected â&#128;&#152;;â&#128;&#153; before â&#128;&#152;sizeâ&#128;&#153;
loadndisdriver.c:68: error: â&#128;&#152;NULLâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of â&#128;&#152;statbufâ&#128;&#153; isnâ&#128;&#153;t known
loadndisdriver.c:71: warning: implicit declaration of function â&#128;&#152;basenameâ&#128;&#153;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function â&#128;&#152;openâ&#128;&#153;
loadndisdriver.c:73: error: â&#128;&#152;O_RDONLYâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â&#128;&#152;syslogâ&#128;&#153;
loadndisdriver.c:75: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:75: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function â&#128;&#152;strerrorâ&#128;&#153;
loadndisdriver.c:75: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:76: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function â&#128;&#152;fstatâ&#128;&#153;
loadndisdriver.c:81: warning: implicit declaration of function â&#128;&#152;closeâ&#128;&#153;
loadndisdriver.c:84: error: â&#128;&#152;sizeâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function â&#128;&#152;mmapâ&#128;&#153;
loadndisdriver.c:86: error: â&#128;&#152;PROT_READâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:86: error: â&#128;&#152;MAP_PRIVATEâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: â&#128;&#152;MAP_FAILEDâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function â&#128;&#152;strncpyâ&#128;&#153;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function â&#128;&#152;strncpyâ&#128;&#153;
loadndisdriver.c:95: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;sizeâ&#128;&#153;
loadndisdriver.c:96: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;dataâ&#128;&#153;
loadndisdriver.c:69: warning: unused variable â&#128;&#152;statbufâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;parse_setting_lineâ&#128;&#153;:
loadndisdriver.c:109: warning: implicit declaration of function â&#128;&#152;isspaceâ&#128;&#153;
loadndisdriver.c:115: warning: implicit declaration of function â&#128;&#152;strchrâ&#128;&#153;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function â&#128;&#152;strchrâ&#128;&#153;
loadndisdriver.c:115: error: â&#128;&#152;NULLâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:117: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:117: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:118: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function â&#128;&#152;strlenâ&#128;&#153;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function â&#128;&#152;strlenâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;read_conf_fileâ&#128;&#153;:
loadndisdriver.c:150: error: storage size of â&#128;&#152;statbufâ&#128;&#153; isnâ&#128;&#153;t known
loadndisdriver.c:151: error: â&#128;&#152;FILEâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:151: error: â&#128;&#152;configâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function â&#128;&#152;lstatâ&#128;&#153;
loadndisdriver.c:158: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:158: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:158: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:160: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function â&#128;&#152;sscanfâ&#128;&#153;
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function â&#128;&#152;sscanfâ&#128;&#153;
loadndisdriver.c:178: warning: implicit declaration of function â&#128;&#152;fopenâ&#128;&#153;
loadndisdriver.c:178: error: â&#128;&#152;NULLâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function â&#128;&#152;fgetsâ&#128;&#153;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function â&#128;&#152;strncpyâ&#128;&#153;
loadndisdriver.c:205: warning: implicit declaration of function â&#128;&#152;fcloseâ&#128;&#153;
loadndisdriver.c:150: warning: unused variable â&#128;&#152;statbufâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;load_bin_fileâ&#128;&#153;:
loadndisdriver.c:217: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:217: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function â&#128;&#152;tolowerâ&#128;&#153;
loadndisdriver.c:221: warning: implicit declaration of function â&#128;&#152;chdirâ&#128;&#153;
loadndisdriver.c:222: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:224: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function â&#128;&#152;strncpyâ&#128;&#153;
loadndisdriver.c:232: warning: implicit declaration of function â&#128;&#152;ioctlâ&#128;&#153;
loadndisdriver.c:232: warning: implicit declaration of function â&#128;&#152;_IOWâ&#128;&#153;
loadndisdriver.c:232: error: expected expression before â&#128;&#152;structâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;load_driverâ&#128;&#153;:
loadndisdriver.c:249: error: â&#128;&#152;DIRâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:249: error: â&#128;&#152;driver_dirâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:251: error: â&#128;&#152;NULLâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:255: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:255: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:257: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:259: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function â&#128;&#152;opendirâ&#128;&#153;
loadndisdriver.c:267: warning: implicit declaration of function â&#128;&#152;mallocâ&#128;&#153;
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function â&#128;&#152;mallocâ&#128;&#153;
loadndisdriver.c:271: warning: implicit declaration of function â&#128;&#152;memsetâ&#128;&#153;
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function â&#128;&#152;memsetâ&#128;&#153;
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function â&#128;&#152;strncpyâ&#128;&#153;
loadndisdriver.c:280: warning: implicit declaration of function â&#128;&#152;readdirâ&#128;&#153;
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of â&#128;&#152;statbufâ&#128;&#153; isnâ&#128;&#153;t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function â&#128;&#152;statâ&#128;&#153;
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function â&#128;&#152;S_ISREGâ&#128;&#153;
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function â&#128;&#152;strlenâ&#128;&#153;
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function â&#128;&#152;strcasecmpâ&#128;&#153;
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function â&#128;&#152;strcpyâ&#128;&#153;
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function â&#128;&#152;strcpyâ&#128;&#153;
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;sizeâ&#128;&#153;
loadndisdriver.c:318: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;dataâ&#128;&#153;
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable â&#128;&#152;statbufâ&#128;&#153;
loadndisdriver.c:344: error: expected expression before â&#128;&#152;structâ&#128;&#153;
loadndisdriver.c:346: warning: implicit declaration of function â&#128;&#152;closedirâ&#128;&#153;
loadndisdriver.c:348: warning: implicit declaration of function â&#128;&#152;freeâ&#128;&#153;
loadndisdriver.c:355: warning: implicit declaration of function â&#128;&#152;munmapâ&#128;&#153;
loadndisdriver.c:355: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;dataâ&#128;&#153;
loadndisdriver.c:355: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;sizeâ&#128;&#153;
loadndisdriver.c:357: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;dataâ&#128;&#153;
loadndisdriver.c:357: error: â&#128;&#152;struct load_driver_fileâ&#128;&#153; has no member named â&#128;&#152;sizeâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;get_deviceâ&#128;&#153;:
loadndisdriver.c:367: error: storage size of â&#128;&#152;statbufâ&#128;&#153; isnâ&#128;&#153;t known
loadndisdriver.c:370: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:370: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:373: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:374: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function â&#128;&#152;snprintfâ&#128;&#153;
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function â&#128;&#152;snprintfâ&#128;&#153;
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function â&#128;&#152;strncpyâ&#128;&#153;
loadndisdriver.c:367: warning: unused variable â&#128;&#152;statbufâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;load_deviceâ&#128;&#153;:
loadndisdriver.c:419: error: â&#128;&#152;DIRâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:419: error: â&#128;&#152;dirâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:423: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:423: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function â&#128;&#152;memsetâ&#128;&#153;
loadndisdriver.c:426: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:427: error: â&#128;&#152;EINVALâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:429: error: â&#128;&#152;NULLâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before â&#128;&#152;structâ&#128;&#153;
loadndisdriver.c: In function â&#128;&#152;get_ioctl_deviceâ&#128;&#153;:
loadndisdriver.c:464: error: â&#128;&#152;FILEâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:464: error: â&#128;&#152;proc_miscâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function â&#128;&#152;strstrâ&#128;&#153;
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function â&#128;&#152;strstrâ&#128;&#153;
loadndisdriver.c:473: warning: implicit declaration of function â&#128;&#152;strtolâ&#128;&#153;
loadndisdriver.c:473: error: â&#128;&#152;NULLâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:483: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:483: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function â&#128;&#152;unlinkâ&#128;&#153;
loadndisdriver.c:489: warning: implicit declaration of function â&#128;&#152;mknodâ&#128;&#153;
loadndisdriver.c:489: error: â&#128;&#152;S_IFCHRâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:489: error: â&#128;&#152;MISC_MAJORâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:490: error: â&#128;&#152;errnoâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:495: error: â&#128;&#152;O_RDONLYâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c: In function â&#128;&#152;mainâ&#128;&#153;:
loadndisdriver.c:511: warning: implicit declaration of function â&#128;&#152;openlogâ&#128;&#153;
loadndisdriver.c:511: error: â&#128;&#152;LOG_PERRORâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#128;&#152;LOG_CONSâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#128;&#152;LOG_KERNâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:511: error: â&#128;&#152;LOG_DEBUGâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:513: error: â&#128;&#152;LOG_INFOâ&#128;&#153; undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function â&#128;&#152;strncmpâ&#128;&#153;
loadndisdriver.c:517: warning: implicit declaration of function â&#128;&#152;printfâ&#128;&#153;
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function â&#128;&#152;printfâ&#128;&#153;
loadndisdriver.c:527: warning: implicit declaration of function â&#128;&#152;atoiâ&#128;&#153;
loadndisdriver.c:542: warning: implicit declaration of function â&#128;&#152;atofâ&#128;&#153;
loadndisdriver.c:549: warning: implicit declaration of function â&#128;&#152;strcmpâ&#128;&#153;
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function â&#128;&#152;sscanfâ&#128;&#153;
loadndisdriver.c:590: warning: implicit declaration of function â&#128;&#152;closelogâ&#128;&#153;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/roberto/ndiswrapper-1.52/utils'
make: *** [install] Error 2

```

* my note is in my job, I dont have internet to him.

---

