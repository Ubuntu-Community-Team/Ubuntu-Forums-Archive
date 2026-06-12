---
title: "Locale error"
date: 2005-01-20
forum: Desktop Environments
---

### Post by Sasayaki on 2005-01-20
This error has persisted since install, and although it doesn't seem critical at the moment, it's still annoying.

The Locale package refuses to install. Here's the output of 'sudo apt-get install locales':

sasayaki@balthazar:/usr/sbin $ sudo apt-get install locales
Reading Package Lists... Done
Building Dependency Tree... Done
locales is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up locales (2.3.2.ds1-13ubuntu2.2) ...
Generating locales...
  Usage:./usr/sbin/validlocale <locale>...Try `localedef --help' or `localedef --usage' for more information.
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on lsb; however:
  Package lsb is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
 lsb
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone know how to fix this so it installs?

---

