---
title: "Is there a GUI firewall for Kubuntu?"
date: 2005-04-09
forum: Desktop Environments
---

### Post by KDE-fan on 2005-04-09
I think I should install a firewall to make it harder to break in to my PC. Is there a firewall with a nice graphical interface for Kubuntu?

---

### Post by p!=f on 2005-04-09
[QUOTE=KDE-fan]I think I should install a firewall to make it harder to break in to my PC. Is there a firewall with a nice graphical interface for Kubuntu?[/QUOTE]
I don't use KDE but quick apt-cache search (you lazy one! :)) gave me this:
> 
[~] > wajig show {guard,guide}dog
Package: guarddog
Priority: optional
Section: universe/net
Installed-Size: 1112
Maintainer: Paul Cupis <paul@cupis.co.uk>
Architecture: i386
Version: 2.3.2-1
Depends: kdelibs4 (>= 4:3.2.3), libart-2.0-2 (>= 2.3.16), libc6 (>= 2.3.2.ds1-4), libfam0c102, libgcc1 (>= 1:3.4.1-3), libice6 | xlibs (>> 4.1.0), libpng12-0 (>= 1.2.5.0-4), libqt3c102-mt (>= 3:3.2.3-3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxrender1, zlib1g (>= 1:1.2.1), gawk
Filename: pool/universe/g/guarddog/guarddog_2.3.2-1_i386.deb
Size: 310206
MD5sum: 76a3309f8f7adf01c04471ae3a675e91
Description: firewall configuration utility for KDE
 Guarddog is a firewall configuration utility for KDE. It is aimed at two
 groups of users: novice to intermediate users who are not experts in TCP/IP
 networking and security, and those users who don't want the hassle of
 dealing with cryptic shell scripts and ipchains/iptables parameters.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: guidedog
Priority: optional
Section: universe/net
Installed-Size: 440
Maintainer: Paul Cupis <paul@cupis.co.uk>
Architecture: i386
Version: 1.0.0-1
Depends: kdelibs4 (>= 4:3.2.3), libart-2.0-2 (>= 2.3.16), libaudio2, libc6 (>= 2.3.2.ds1-4), libfam0c102, libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:3.3.4-1), libice6 | xlibs (>> 4.1.0), libpng12-0 (>= 1.2.5.0-4), libqt3c102-mt (>= 3:3.2.3-3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxmu6 | xlibs (>> 4.1.0), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), xlibmesa-gl | libgl1, zlib1g (>= 1:1.2.1), gawk, iptables
Suggests: guarddog
Filename: pool/universe/g/guidedog/guidedog_1.0.0-1_i386.deb
Size: 124448
MD5sum: 8bbb78c07bb027fb3f10c93bc9d2cbc5
Description: NAT/masquerading/port-forwarding configuration tool for KDE
 Guidedog is a KDE utility which allows to use easily activate and
 configure your machine for packet routing, Network Address
 Translation/IP Masquerading (NAT) and port-forwarding.
 .
 If you are using the functions of this program, it is recommended that
 you setup/configure a firewall to protect your machine - guidedog does
 not setup a firewall for you. To configure a firewall, the Guarddog
 program, by the same author, is recommended.
 .
 Guidedog requires iptables, and therefore Linux kernel 2.4+.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


---

### Post by sinbad782 on 2005-04-10
Yup, Gaurddog is quite nice. Firestarter is also very easy to use. 

I have also played around with firewall builder in the past too, as this seems more flexible.

---

### Post by sinbad782 on 2005-04-10
whoops - I meant guarddog!

---

### Post by meldroc on 2005-04-10
[QUOTE=sinbad782]whoops - I meant guarddog![/QUOTE]
 Yep, guarddog is quite nice for setting up a basic firewall - lets you set up zones so you can allow traffic from certain IP addresses, but not other, lets you do usual stuff like blocking by port.

---

