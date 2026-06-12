---
title: "/usr/bin/dpkg returned an error code (1)"
date: 2006-08-09
forum: Desktop Environments
---

### Post by vikashtiwari on 2006-08-09
whener i try to install anything using apt-get  or synaptic , i get following error
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ciscosurfer on 2006-08-09
Make sure you don't use apt-get and synaptic at the same time.  Use one or the other, then be sure to update your repositories and then install.  

Try this first:

At the command line```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by vikashtiwari on 2006-08-10
vikash@google:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up openoffice.org-common (2.0.2-2ubuntu12.1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 476 strings at 20 - 2788
Wrote aliases at 2788 - 2934
Wrote parents at 2934 - 32e4
Wrote literal globs at 32e4 - 3340
Wrote suffix globs at 3340 - 6688
Wrote full globs at 6688 - 66ac
Wrote magic at 66ac - bcf8
Wrote namespace list at bcf8 - bd08
***
update-xmlcatalog: error: local catalog /usr/share/xml/openoffice.org-common/catalog.xml not found
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common (>> 2.0.2); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base (>> 2.0.2); however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up openoffice.org-common (2.0.2-2ubuntu12.1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 476 strings at 20 - 2788
Wrote aliases at 2788 - 2934
Wrote parents at 2934 - 32e4
Wrote literal globs at 32e4 - 3340
Wrote suffix globs at 3340 - 6688
Wrote full globs at 6688 - 66ac
Wrote magic at 66ac - bcf8
Wrote namespace list at bcf8 - bd08
***
update-xmlcatalog: error: local catalog /usr/share/xml/openoffice.org-common/catalog.xml not found
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common (>> 2.0.2); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-base (>> 2.0.2); however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-base
 openoffice.org
 openoffice.org-evolution
vikash@google:~$

---

### Post by vikashtiwari on 2006-08-10
error: local catalog /usr/share/xml/openoffice.org-common/catalog.xml not found


there is no oprnoffice.org directory in that given path.... 
i think i need to reinstall os..nobody seems to be interested in this problem

---

