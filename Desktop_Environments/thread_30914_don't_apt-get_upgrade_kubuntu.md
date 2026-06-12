---
title: "don't apt-get upgrade kubuntu"
date: 2005-05-01
forum: Desktop Environments
---

### Post by jamez on 2005-05-01
Preconfiguring packages ...
(Reading database ... 58686 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Can we get this fixed please? I know I can't be the only one getting this error on 2 different desktops and 1 laptop, so it must be a system-wide bug.

Thanks!  ;-)

---

### Post by jodef on 2005-05-01
Try doing a search in the forums I recall seeing users reporting a similar problem I am not 100% sure ah found it check the info in these threads :
[Kde-libs error](http://www.ubuntuforums.org/showthread.php?t=29771&highlight=upgrade+errors+kde) 
[Kde Upgrade Errors](http://ubuntuforums.org/showthread.php?t=25294)

---

### Post by Gezzer on 2005-05-01
[QUOTE=jamez]Preconfiguring packages ...
(Reading database ... 58686 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Can we get this fixed please? I know I can't be the only one getting this error on 2 different desktops and 1 laptop, so it must be a system-wide bug.

Thanks!  ;-)[/QUOTE]
 uninstall knetworkconf
install the updates
reinstall knetworkconf ...

---

