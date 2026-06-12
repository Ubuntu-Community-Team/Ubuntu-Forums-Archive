---
title: "restore desktop environment selection in lightdm in bionic"
date: 2019-01-07
forum: Desktop Environments
---

### Post by lvm on 2019-01-07
I have KDE and xfce installed on the same machine. On xenial and before I was able to select the environment when logging in. Upgrade to bionic killed lightdm, this bug is known ([https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1770965](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1770965)) and the recommended fix is to install lightdm-gtk-greeter instead of the obsoleted lightdm-kde-greeter. It recovered the system but now it always boots to xfce and there is no way to select KDE. How can I fix it?

---

### Post by mahardi-baniadam on 2019-01-07
have you tried resinstall KDE environment?

---

