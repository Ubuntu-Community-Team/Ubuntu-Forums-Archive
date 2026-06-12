---
title: "Mono wants to uninstall desktop"
date: 2006-08-18
forum: Desktop Environments
---

### Post by t_ras on 2006-08-18
I did dist upgrade and got this:
```
root@terrenisrv1:/home/martint# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages will be REMOVED
  gnome-rdp gnome-terminal ubuntu-desktop
The following NEW packages will be installed
  libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-peapi1.0-cil
  libmono-relaxng1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil
  libmono-system-data1.0-cil libmono-system-runtime1.0-cil
  libmono-system-web1.0-cil libmono-system1.0-cil libmono1.0-cil mono-gac
  mono-runtime
The following packages have been kept back:
  libvte-common
The following packages will be upgraded:
  gnome-terminal-data mono-classlib-1.0 mono-mcs
3 upgraded, 13 newly installed, 3 to remove and 1 not upgraded.
Need to get 9114kB of archives.
After unpacking 1346kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

will I realy loose my desktop? 
why it wants to remove it?

THANKS!!

---

### Post by kaffelars on 2006-08-18
The Ubuntu-desktop package is actually a metapackage. Installing it means installing all the default packages automatically.
Uninstalling it howevere, will **not** uninstall anything else than the package itself.

For instance, Ubuntu-desktop requires Evolution, as this is the default e-mail client in Ubuntu. If I want to uninstall Evolution, I'll have to uninstall both Ubuntu-desktop and Evolution (but no other packages are affected).

Said in less words, the Ubuntu-desktop package is safe to delete.

---

### Post by t_ras on 2006-08-18
Thanks!

---

