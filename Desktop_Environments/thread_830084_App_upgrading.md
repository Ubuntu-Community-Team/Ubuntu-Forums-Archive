---
title: "App upgrading"
date: 2008-06-15
forum: Desktop Environments
---

### Post by sventer on 2008-06-15
Hi

I'm new to the Linux OS and need help with updating an application.

I installed bouml from the DVD but found a new version. I updated the Software Resources and when I go to the Synaptic Package Manager it is listed for upgrade. But one of the dependencies bouml-core can't be installed:

error message states:
bouml-core:
 PreDepends: x11-utils  but it is not installable

How do I correct this problem?

Thanks

---

### Post by damis648 on 2008-06-15
Click the following: [http://mirrors.kernel.org/ubuntu/pool/main/x/x11-utils/x11-utils_7.3+1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/x11-utils/x11-utils_7.3+1_i386.deb) and open it in "Gdebi Package Installer" and install it. Then try updating again.

---

### Post by sventer on 2008-06-15
Hi damis648

I tried what you suggested but I get Error conflict with installed packages.

---

### Post by damis648 on 2008-06-15
That is interesting... try going into synaptic and fixing broken packages and try upgrading your app again.

---

