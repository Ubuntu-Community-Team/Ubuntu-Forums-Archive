---
title: "Compiz Fusion comes back after reinstall??"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by daveluke on 2008-02-23
So I installed compiz fusion and played around with the effects... I got carried away with all the effects and tried to do that nautilus hack that gives you different wallpapers on each workspace and messed something up... Then everything seemed to work, but was very slow... so eventually I just reinstalled Ubuntu completely which wiped out everything on my hard drive (?)

After the reinstall, everything seemed to run quickly... One thing I noticed is the option in Administration > Login Screen wasn't there, which I assumed was a feature of Compiz Fusion.. Also the Super+E and Super+Tab feature wasn't working anymore.. These I assume are also features of Compiz Fusion.. Then my computer froze up, and when I turned off/turned back on the computer, these features were enabled... However, there are no custom/advanced visuals in the appearance screen. no emerald thingy neither...

Did something not get removed when I reinstalled?

Thanks in advance.. I really am a beginner with Linux and have been kinda install-happy with all the plugins and effects...

---

### Post by applehead on 2008-02-23
Sound odd,  what version of ubuntu is it?

---

### Post by daveluke on 2008-02-23
It's 7.10 Gutsy...

When I do a locate fusion, the following shows up:
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/spi.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/ctl.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/max
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/max/sge.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/fc.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/sas.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion/lan.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/fusion.h
/usr/src/linux-headers-2.6.22-14/drivers/message/fusion
/usr/src/linux-headers-2.6.22-14/drivers/message/fusion/Kconfig
/usr/src/linux-headers-2.6.22-14/drivers/message/fusion/Makefile
/usr/lib/libfusion-0.9.so.25.0.0
/usr/lib/libfusion-0.9.so.25
/usr/share/doc/compiz-fusion-plugins-extra
/usr/share/doc/compiz-fusion-plugins-extra/changelog.Debian.gz
/usr/share/doc/compiz-fusion-plugins-extra/copyright
/usr/share/doc/compiz-fusion-plugins-extra/NEWS.gz
/usr/share/doc/compiz-fusion-plugins-extra/AUTHORS
/usr/share/doc/compiz-fusion-plugins-main
/usr/share/doc/compiz-fusion-plugins-main/changelog.Debian.gz
/usr/share/doc/compiz-fusion-plugins-main/copyright
/usr/share/doc/compiz-fusion-plugins-main/NEWS.gz
/usr/share/doc/compiz-fusion-plugins-main/AUTHORS
/usr/share/compiz/fusioncap.png
/var/lib/dpkg/info/compiz-fusion-plugins-extra.md5sums
/var/lib/dpkg/info/compiz-fusion-plugins-main.md5sums
/var/lib/dpkg/info/compiz-fusion-plugins-main.list
/var/lib/dpkg/info/compiz-fusion-plugins-extra.list
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptsas.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptspi.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptfc.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptlan.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptctl.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptbase.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/message/fusion/mptscsih.ko

Does this mean that the reinstall of Ubuntu did not wipe out everything?

In any case, how can I uninstall compiz fusion? My computer runs a lot faster without it.

Thanks.

---

### Post by fracturedmorals on 2008-02-23
Perhaps you had an error during installation?

Have you checked the integrity of your gutsy CD?

---

