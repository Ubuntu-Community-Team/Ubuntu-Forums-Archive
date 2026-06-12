---
title: "Can't access package manager (adept)"
date: 2008-12-24
forum: General Help
---

### Post by Cotopaxi on 2008-12-24
I can't access the package manager under kubuntu 8.10.

When I try to access, selecting the package manager icon from the menu, I get an error message similar to: "Can't lock up cache memory, the program can only be executed in read only mode".

When I try to acces the package manager via the terminal (sudo adept), I get the following error message:

> systemverwaltung@systemverwaltung-desktop:~$ sudo adept
[sudo] password for systemverwaltung:
Error: "/var/tmp/kdecache-systemverwaltung" is owned by uid 1000 instead of uid0.
Error: "/tmp/kde-systemverwaltung" is owned by uid 1000 instead of uid 0.
Constructing PkgSystem
Error: "/tmp/ksocket-systemverwaltung" is owned by uid 1000 instead of uid 0.
adept(5636) KToolInvocation::klauncher: klauncher not running... launching kdeinit
Error: "/tmp/kde-systemverwaltung" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-systemverwaltung" is owned by uid 1000 instead of uid 0.
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
Error: "/tmp/ksocket-systemverwaltung" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-systemverwaltung" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kded4
Error: "/var/tmp/kdecache-systemverwaltung" is owned by uid 1000 instead of uid0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-systemverwaltung" is owned by uid 1000 instead of uid0.
Error: "/var/tmp/kdecache-systemverwaltung" is owned by uid 1000 instead of uid0.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update
kdeinit4: preparing to launch
PkgSystem Score:32


Any idea what's going on?

Thanks!

---

