---
title: "gammu ?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by sles on 2006-08-25
Hello!

As I see there is no packages for ubuntu.
And I can't install package from debian (gammu needs libbluetooth2):

 dpkg -i libbluetooth2_3.1-1_i386.deb
(Reading database ... 99290 files and directories currently installed.)
Preparing to replace libbluetooth2 3.1-1 (using libbluetooth2_3.1-1_i386.deb) ...
Unpacking replacement libbluetooth2 ...
dpkg: dependency problems prevent configuration of libbluetooth2:
 libbluetooth2 depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing libbluetooth2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libbluetooth2

If I say to dpkg to ignore dependency than Synaptic says that I have errors and wants to uninstall package.
How can I solve this problem?
btw, I tried to build debs for bluez-libs from sources, but, unfortunately, failed -  I'm newbie :-(
 dpkg-buildpackage -rfakeroot created empty packages for some reasons and I can't find these reasons :-(
May be somebody already has gammu for ubunty?

---

