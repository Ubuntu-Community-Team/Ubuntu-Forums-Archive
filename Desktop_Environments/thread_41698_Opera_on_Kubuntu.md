---
title: "Opera on Kubuntu"
date: 2005-06-14
forum: Desktop Environments
---

### Post by HappyPaul on 2005-06-14
Hello:

I have installed Kubuntu on both my IBM ThinkPad (A20m) and my G3 iMac.  So far, so good.  I'd like to install my favourite web browser, Opera, on both systems and was wondering if anybody knows which is the best version of Opera to download for Kubuntu, i.e. static DEB, static RPM, TarBall et cetera?  I realize I need i386 for the Laptop and PowerPC for the iMac.

Thanks,

Paul

---

### Post by snds24 on 2005-06-14
[QUOTE=HappyPaul]Hello:

I have installed Kubuntu on both my IBM ThinkPad (A20m) and my G3 iMac.  So far, so good.  I'd like to install my favourite web browser, Opera, on both systems and was wondering if anybody knows which is the best version of Opera to download for Kubuntu, i.e. static DEB, static RPM, TarBall et cetera?  I realize I need i386 for the Laptop and PowerPC for the iMac.

Thanks,

Paul[/QUOTE]
 I use opera-static_8.01-20050602.1-qt_en_i386.deb and it works without problems.

---

### Post by Xian on 2005-06-14
The static version will work but your menu fonts will not look very good. I use the [shared-qt_en_sarge_i386.deb](ftp://ftp.opera.com/pub/opera/linux/800/final/en/i386/shared/opera_8.0-20050415.6-shared-qt_en_sarge_i386.deb) package and it works great, but you will also need to install the libqt3c102-mt package in Synaptic to get all the shared libraries in line.

---

### Post by qalimas on 2005-06-14
I installed the Sarge 3.1 package from the Debian list.  Works great.

---

### Post by eric390d on 2005-06-30
is it possible to get the menus to look better? I installed the static package first then the shared and they look exactly the same.

---

### Post by haaglin on 2005-07-01
[QUOTE=eric390d]is it possible to get the menus to look better? I installed the static package first then the shared and they look exactly the same.[/QUOTE]

Try using qtconfig, $apt-get install qt3-qtconfig.

---

