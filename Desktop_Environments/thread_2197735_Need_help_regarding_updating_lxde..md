---
title: "Need help regarding updating lxde."
date: 2014-01-05
forum: Desktop Environments
---

### Post by arroy_0209 on 2014-01-05
I upgraded from ubuntu 10.04 to 12.04 and installed lxde desktop long ago. I do not remember exactly how I installed it and I have never received security or any other updates of lxde (but I do receive lots of ubuntu updates which I receive regularly). The command "apt-cache policy lxde" shows:
> 
lxde:
  Installed: 0.5.0-4ubuntu3
  Candidate: 0.5.0-4ubuntu3
  Version table:
 *** 0.5.0-4ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status

However if I right click on the panel and choose panel option, a new window opens informing that I am using LXpanel 0.5.8. I am confused here also; exactly which version am I using currently, 0.5.0 or 0.5.8? 
My question is, how should I ensure that I receive security and other necessary updates of lxde? (Please note I do not remember whether I installed lxde from ubuntu repository or from lxde homepage) Will I have to uninstall existing version of lxde and do a reinstallation?

---

### Post by Dennis N on 2014-01-05
Both packages are current versions. LXDE is a metapackage bringing many different packages of that desktop environment with it when installed. lxde-common and lxde-core have the same version number as the lxde metapackage. If you check the current version numbers of the other components it brings to your system, there is no necessary agreement.

The ubuntu repository is marked as the source (with ***) in your display. Updates will come from there. If there are any, they will be offered.

---

### Post by bapoumba on 2014-01-05
A useful page to bookmark when you want to check packages versions for a release : [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

[http://packages.ubuntu.com/search?suite=precise&section=all&arch=any&keywords=lxde&searchon=names](http://packages.ubuntu.com/search?suite=precise&section=all&arch=any&keywords=lxde&searchon=names)
[http://packages.ubuntu.com/search?suite=precise&section=all&arch=any&keywords=lxpanel&searchon=names](http://packages.ubuntu.com/search?suite=precise&section=all&arch=any&keywords=lxpanel&searchon=names)

---

### Post by arroy_0209 on 2014-01-05
Thanks for such quick responses. 
I notice that the package was installed from universe but it appears that universe is not providing the latest official version of lxde.

---

### Post by bapoumba on 2014-01-05
You have the package for your release. For ex, I have on 13.10 :
```
apt-cache show lxde
Package: lxde
Priority: optional
Section: universe/x11
Installed-Size: 30
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian LXDE Packaging Team <pkg-lxde-maintainers@lists.alioth.debian.org>
Architecture: all
Source: lxde-common
Version: 0.5.0-4ubuntu4

```

---

### Post by arroy_0209 on 2014-01-05
Ok, that means version of lxde is fixed for a particular release of ubuntu. Even if newer versions of lxde are released, ubuntu will not ask users to update (unlike e.g., firefox). But is it not risky to use older versions from security (and functional) point of view?

---

### Post by Dennis N on 2014-01-05
If there was a security risk, it would also be fixed in all the available versions, not just the newest. For some new feature in a newer version, you will have to wait, or maybe find a newer version offered in a PPA. Libre Office does this, for example.

---

