---
title: "[SOLVED] lenny live cd woes"
date: 2008-02-02
forum: Debian
---

### Post by maybeway36 on 2008-02-02
I'm trying to make a Debian lenny (testing) live CD with live-helper. I follow these commands:
```
mkdir lennycd
cd lennycd
lh_config
sudo lh_build
```
But running the CD in qemu gives me this:
[[IMG]http://img110.imageshack.us/img110/3315/cdzp2.png[/IMG]](http://img110.imageshack.us/my.php?image=cdzp2.png)
What gives? Is this just a temporary lenny problem, like the sort of thing you see in sid (bugs popping up and going away?)

---

### Post by maybeway36 on 2008-02-05
What seemed to fix it was installing the user-setup from sid in the chroot.
Get this:
[ftp://ftp.us.debian.org/debian/pool/main/u/user-setup/user-setup_1.18_all.deb]("ftp://ftp.us.debian.org/debian/pool/main/u/user-setup/user-setup_1.18_all.deb")
Put it in config/chroot_local-packages and build.
Also see: [http://lists.alioth.debian.org/pipermail/debian-live-devel/2008-February/003050.html]("http://lists.alioth.debian.org/pipermail/debian-live-devel/2008-February/003050.html")

---

### Post by init1 on 2008-02-05
wait, so did you solve it already? I use the Etch backport for live-helper, so you may want to try that in any case.

---

### Post by polmir on 2008-02-06
Tray with new kernel
```
wget http://www.eu.kernel.org/pub/linux/kernel/v2.6/linux-2.6.24.tar.bz2
```

---

