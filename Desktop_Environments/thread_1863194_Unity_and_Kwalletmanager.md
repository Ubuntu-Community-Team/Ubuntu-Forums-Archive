---
title: "Unity and Kwalletmanager"
date: 2011-10-17
forum: Desktop Environments
---

### Post by lovinglinux on 2011-10-17
I am migrating from KDE to Unity. I still use some KDE applications and some of them have passwords stored on kwallet. Additionally, I also have some custom passwords saved in my wallets.

The thing is that kwalletmanager runs in KDE panel tray and when launched through Unity, there is no way to click it to open the wallet manager.

So, I am looking for a way to open my wallets without relying on the kwallet tray launcher. I also don't want to install the kde desktop just to retrieve my passwords.

Any ideas?

If nobody knows how to do this, I will probably install Kubuntu on a VM and copy my wallet there, but I would prefer a permanent and integrated solution.

---

### Post by PhoneixS on 2012-05-24
Try this little script or execute it manually.

```
#/bin/bash
/bin/kill `/bin/ps aux |/bin/grep kwalletmanager|/usr/bin/awk '{print $2}'`; /usr/bin/kwalletmanager --show

```It's related to bug [https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/576284](https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/576284).

---

