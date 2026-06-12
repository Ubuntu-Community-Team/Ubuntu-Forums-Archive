---
title: "Synaptic Problems"
date: 2005-02-08
forum: Desktop Environments
---

### Post by totalshredder on 2005-02-08
Hey Everybody!

  I have a problem. I've been trying to use synaptic to upgrade things for Ibuntu, it downloads the files fine, but every single time I get the same errors:

```
root@ubuntu:/home/luke # apt-get install libice-dev
Reading Package Lists... Done
Building Dependency Tree... Done
libice-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gs-esp (7.07.1-9ubuntu2) ...
/usr/share/doc-base/gs-esp: cannot open control file for reading: No such file or directory
dpkg: error processing gs-esp (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ijsgimpprint:
 ijsgimpprint depends on gs (>= 6.53) | gs-esp (>= 6.53) | gs-aladdin (>= 7.04); however:
  Package gs is not installed.
  Package gs-esp is not configured yet.
  Package gs-aladdin is not installed.
dpkg: error processing ijsgimpprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys:
 cupsys depends on gs-esp; however:
  Package gs-esp is not configured yet.
dpkg: error processing cupsys (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-gimp-print:
 foomatic-db-gimp-print depends on ijsgimpprint (>= 4.2.6-5ubuntu2); however:
  Package ijsgimpprint is not configured yet.
dpkg: error processing foomatic-db-gimp-print (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on gs-esp (>= 7.05) | gs-gpl (>= 6.53) | gs-afpl (>= 7.04-2); however:
  Package gs-esp is not configured yet.
  Package gs-gpl is not installed.
  Package gs-afpl is not installed.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on hpijs (>> 1.3); however:
  Package hpijs is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-gv:
 gnome-gv depends on gs-esp | gs; however:
  Package gs-esp is not configured yet.
  Package gs is not installed.
  Package gs-esp which provides gs is not configured yet.
dpkg: error processing gnome-gv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pnm2ppa:
 pnm2ppa depends on gs; however:
  Package gs is not installed.
  Package gs-esp which provides gs is not configured yet.
dpkg: error processing pnm2ppa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on foomatic-db-gimp-print; however:
  Package foomatic-db-gimp-print is not configured yet.
 ubuntu-desktop depends on foomatic-db-hpijs; however:
  Package foomatic-db-hpijs is not configured yet.
 ubuntu-desktop depends on gnome-gv; however:
  Package gnome-gv is not configured yet.
 ubuntu-desktop depends on pnm2ppa; however:
  Package pnm2ppa is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gs-esp
 ijsgimpprint
 cupsys
 foomatic-db-gimp-print
 hpijs
 foomatic-db-hpijs
 gnome-gv
 pnm2ppa
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

How common is this? Can I fix it? Do I need to re-install ubuntu?

Thanks!
Luke Demi

---

