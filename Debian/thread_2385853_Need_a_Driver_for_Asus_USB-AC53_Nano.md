---
title: "Need a Driver for Asus USB-AC53 Nano"
date: 2018-02-25
forum: Debian
---

### Post by makkuro.kishin on 2018-02-25
Hello, jeremyb31.

I've tried building a driver from both git repositories (jeremyb31 and bijju) in Debian 9 "Stretch" with kernel 4.9.65 and faced the same error as avcat:

1. Building code from [https://github.com/jeremyb31/rtl8822bu.git](https://github.com/jeremyb31/rtl8822bu.git)
```

/home/kishin/exchange/rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6161:25: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .change_virtual_intf = cfg80211_rtw_change_iface,
                         ^~~~~~~~~~~~~~~~~~~~~~~~~
/home/kishin/exchange/rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6161:25: note: (near initialization for ‘rtw_cfg80211_ops.change_virtual_intf’)
/home/kishin/exchange/rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6184:22: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .add_virtual_intf = cfg80211_rtw_add_virtual_intf,
                      ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/home/kishin/exchange/rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6184:22: note: (near initialization for ‘rtw_cfg80211_ops.add_virtual_intf’)
cc1: some warnings being treated as errors
/usr/src/linux-headers-4.9.0-4-common/scripts/Makefile.build:298: recipe for target '/home/kishin/exchange/rtl8822bu-master/os_dep/linux/ioctl_cfg80211.o' failed
make[4]: *** [/home/kishin/exchange/rtl8822bu-master/os_dep/linux/ioctl_cfg80211.o] Error 1
/usr/src/linux-headers-4.9.0-4-common/Makefile:1510: recipe for target '_module_/home/kishin/exchange/rtl8822bu-master' failed
make[3]: *** [_module_/home/kishin/exchange/rtl8822bu-master] Error 2
Makefile:150: recipe for target 'sub-make' failed
make[2]: *** [sub-make] Error 2
Makefile:8: recipe for target 'all' failed
make[1]: *** [all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.9.0-4-amd64'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2

```

2. Building code from [https://github.com/bijju/Asus_USB-AC53_rtl8822bu.git](https://github.com/bijju/Asus_USB-AC53_rtl8822bu.git)
```

/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6884:25: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .change_virtual_intf = cfg80211_rtw_change_iface,
                         ^~~~~~~~~~~~~~~~~~~~~~~~~
/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6884:25: note: (near initialization for ‘rtw_cfg80211_ops.change_virtual_intf’)
/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6907:22: error: initialization from incompatible pointer type [-Werror=incompatible-pointer-types]
  .add_virtual_intf = cfg80211_rtw_add_virtual_intf,
                      ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master/os_dep/linux/ioctl_cfg80211.c:6907:22: note: (near initialization for ‘rtw_cfg80211_ops.add_virtual_intf’)
cc1: some warnings being treated as errors
/usr/src/linux-headers-4.9.0-4-common/scripts/Makefile.build:298: recipe for target '/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master/os_dep/linux/ioctl_cfg80211.o' failed
make[4]: *** [/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master/os_dep/linux/ioctl_cfg80211.o] Error 1
/usr/src/linux-headers-4.9.0-4-common/Makefile:1510: recipe for target '_module_/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master' failed
make[3]: *** [_module_/home/kishin/exchange/Asus_USB-AC53_rtl8822bu-master] Error 2
Makefile:150: recipe for target 'sub-make' failed
make[2]: *** [sub-make] Error 2
Makefile:8: recipe for target 'all' failed
make[1]: *** [all] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.9.0-4-amd64'
Makefile:1801: recipe for target 'modules' failed
make: *** [modules] Error 2

```

My kernel:
```

Linux kishin-lt 4.9.0-4-amd64 #1 SMP Debian 4.9.65-3 (2017-12-03) x86_64 GNU/Linux
gcc version 6.3.0 20170516 (Debian 6.3.0-18)

```

I have a strong feeling that this error can be fixed with a certain patch but I'm no dev and can't come up with it.
Can you please assist with this, cause I'm kind of out of option here? ((

Thanks in advance.

---

### Post by wildmanne39 on 2018-02-25
*Thread moved to **Debian, a more appropriate forum**.*

---

### Post by T.J. on 2018-03-20
Hi!

Generally speaking, you should avoid patching code yourself unless you are willing to accept instability in your system.  In this case, the programmer was a bit sloppy and when writing the code, and  apparently did not do initialization properly.   I *might* be able to fix it for you, but I think it is very possible that you might be able to avoid this altogether by getting code from the Debian or Ubuntu repository.  If you can give me some more background on what you are trying to do, I can be of greater help.  There are some toolchain differences between Debian and Ubuntu.

---

### Post by 6zayn on 2018-09-28
[COLOR=#000000]The programmer was a bit sloppy and when writing the code, and apparently did not do initialization properly. [/COLOR][[color=black]VMate[/color]](https://vidmate.onl/vmate/) [[color=black]9apps[/color]](https://9apps.ooo/download/) [[color=black]Lucky Patcher[/color]](https://luckypatcher.pro/apk/)

---

