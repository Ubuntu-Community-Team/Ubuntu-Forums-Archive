---
title: "Compiling kernel modules (GCC3.4 / 4.0) problem"
date: 2005-10-17
forum: Desktop Environments
---

### Post by nobby_trussin on 2005-10-17
Hi, i thought i would start a new thread for the problem that seems to be plaguing everyone who tries to compile kernel modules in Breezy.

i have read that kernel modules must be compiled with the same version of the compiler the kernel was compiled with (stands to reason) and that this is the reason people are having troubles with breezy as the kernel was compiled using gcc 3.4 and everything else was compiled in 4.0. Therefore i installed gcc-3.4 and made sure that was definitely the default compiler but i still cannot compile. however this module (3com wireless driver) compiled fine under ubuntu 5.04.

its definitely finding the right compiler but now it comes up with a page full of warnings on compilation and says Error [1] and exits

is there anything i can do? i need to get that device working or linux is useless to me. any suggestions would be great?

cheers

Dan

---

### Post by GeneralZod on 2005-10-17
Hi there,

Please can you post the *full* output from the compiler?

---

### Post by blastus on 2005-10-17
I have the [EXACT same problem!](http://ubuntuforums.org/showthread.php?t=77537) I am totally new to this but I also assumed that kernel modules must be compiled with the same compiler version that the kernel was compiled with. I can compile the Lucent modem drivers for Hoary but not for Breezy (I have tried both Kubuntu and just recently Ubuntu.)

```
sudo apt-get install build-essential linux-headers-2.6.12-9-386

cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

gcc -dumpversion
4.0.2
```

As one can see, the kernel was compiled with gcc 3.4.5 but the distribution contains gcc 4.0.2. And here's what I get when I compile the Lucent modem drivers on Breezy...

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/neo/data/ltmodem-2.6-alk-7 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/neo/data/ltmodem-2.6-alk-7/lt_modem.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/neo/data/ltmodem-2.6-alk-7/lt_modem.o] Error 127
make[1]: *** [_module_/home/neo/data/ltmodem-2.6-alk-7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [module] Error 2
```

I see someone has already tried to install gcc 3.4 with no success so I'm not even going to try to install to it (I don't have Internet access in Breezy anyway.) I have no idea how to recompile the kernel so that it is gcc 4.0.2 compatible and don't want to mess with that. Can someone help us out? :???:

---

### Post by nobby_trussin on 2005-10-17
this is the full output: bear in mind that this compiled first time under ubuntu 5.04:

dan@dan:~/Desktop/linux_3CRUSB10075_drv_1_2_0_0$ make
/lib/modules/2.6.12-9-386/build
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0
-I/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.o
In file included from /home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:41:
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.h:675: warning: `__packed__' attribute ignored
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:257: warning: function declaration isn't a prototype
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:258: warning: function declaration isn't a prototype
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `iLED_ON':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.h:1229: sorry, unimplemented: inlining failed in call to 'zd_readl': function body not available
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:453: sorry, unimplemented: called from here
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.h:1230: sorry, unimplemented: inlining failed in call to 'zd_writel': function body not available
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:455: sorry, unimplemented: called from here
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_house_keeping':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:1222: warning: unused variable `tmpvalue'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_transmit_cleanup':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:1689: warning: unused variable `i'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_tx_isr':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:1741: warning: unused variable `next_sw_tcb'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_start_ru':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:2770: warning: unused variable `tmp_value'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:2778: warning: unused variable `loopCnt'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_recycle_rx':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:2869: warning: unused variable `tmp_value'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:2873: warning: unused variable `buffer_found'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_rx_isr':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:3201: warning: ISO C90 forbids mixed declarations and code
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_sleep_reset':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:4650: warning: unused variable `flags'

/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_process_wakeup':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:4803: warning: unused variable `TSFTimer'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:4804: warning: unused variable `tmpvalue'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_watchdog':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5163: warning: unused variable `cbTemp'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5164: warning: unused variable `ssidLenToDump'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5095: warning: unused variable `i'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5096: warning: unused variable `diffTime'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5099: warning: unused variable `tmpvalue'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_ioctl_setiwencode':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5568: warning: unused variable `bReconnect'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205wext_siwscan':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6535: warning: unused variable `i'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6536: warning: unused variable `ul_mac_ps_state'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_translate_scan':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6611: warning: unused variable `macp'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_ioctl':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6892: warning: ISO C90 forbids mixed declarations and code
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6921: warning: ISO C90 forbids mixed declarations and code
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:7096: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_load_card_setting':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:7698: warning: suggest parentheses around assignment used as truth value
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:7651: warning: unused variable `file_info'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:7654: warning: unused variable `j'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_save_card_setting':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:7776: warning: unused variable `file_info'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:7779: warning: unused variable `i'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zd1205_clear_structs':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:8024: warning: unused variable `macp'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `zdcb_setup_next_send':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:8138: warning: unused variable `next_sw_tcb'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:8144: warning: unused variable `tmp_value'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:8144: warning: unused variable `tmp_value3'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:8156: warning: unused variable `lock_flag'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:8158: warning: unused variable `loopCnt'
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: In function `CalculateQuality':
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:9302: warning: ISO C90 forbids mixed declarations and code
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c: At top level:
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:5859: warning: 'zd1205_ioctl_getsens' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6290: warning: 'zd1205wext_giwname' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6315: warning: 'zd1205wext_siwfreq' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6374: warning: 'zd1205wext_siwrate' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6402: warning: 'zd1205wext_siwrts' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6417: warning: 'zd1205wext_siwfrag' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6424: warning: 'zd1205wext_giwtxpow' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6431: warning: 'zd1205wext_siwtxpow' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6437: warning: 'zd1205wext_giwap' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6452: warning: 'zd1205wext_siwencode' defined but not used
/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.c:6460: warning: 'zd1205wext_giwencode' defined but not used
make[2]: *** [/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.o] Error 1
make[1]: *** [_module_/home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [all] Error 2

---

### Post by nobby_trussin on 2005-10-18
no clues on this one? anyone? PLEASE? :)

only kidding but i really am stuck on this. and there was me thinking i was actually half decent and linux stuff

---

### Post by ssierra on 2005-10-18
This is a problem that is happening in all the new distributions. I am having the same problem in SUSE 10, and for this reason i am not tring to compile new modules agains we can have a solution.

Regards

---

### Post by GeneralZod on 2005-10-18
Nasty one :)

Google tells me that the line 

```

sorry, unimplemented: inlining failed in call to 'zd_readl': function body not available

```

is the line causing the failure (usually such lines have a nice, handy, "Error:" mark next to them, but not this time, apparently :))

It is possible that simply removing occurrences of the word

```

inline

```

from /home/dan/Desktop/linux_3CRUSB10075_drv_1_2_0_0/src/zd1205.h will fix this, but I am most definitely *not* recommending this course of action :) Try at your own risk ;)

---

