---
title: "safe to remove kubuntu-desktop from within Adept?"
date: 2006-11-01
forum: Desktop Environments
---

### Post by tubunu on 2006-11-01
In Adept Installer I've decided to uninstall some of the programmes I don't use, e.g. kdebluetooth and kppp. After inspecting changes and applying, the list  of packages to remove includes **kubuntu-desktop**. Is it safe to delete? Will I be able to boot to my desktop aferwards?

---

### Post by meng on 2006-11-01
Yes it is safe, kubuntu-desktop is an empty package (meta-package) which lists many other packages as dependencies, for ease of INSTALLING (to install, you simply select the package kubuntu-desktop). It creates confusion on UNINSTALLING some of those dependencies, because it makes users suspect that they are about to lose KDE altogether. This won't happen, don't worry about it.

Think of kubuntu-desktop as a cardboard box that comes filled with all the KDE goodies. Removing kubuntu-desktop just throws out the box (but that's empty anyway).

---

### Post by tubunu on 2006-11-01
Thanks!

---

