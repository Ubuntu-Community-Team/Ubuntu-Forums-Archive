---
title: "issues with brother DCP-130C Multifunction printer scanner"
date: 2011-07-18
forum: Desktop Environments
---

### Post by geofferygordon on 2011-07-18
the issue is I'm attempting to install the current brother drivers but it wont work here is the terminal response im getting:

sudo apt-get  install brother-lpr-drivers-bh7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  brother-lpr-drivers-bh7
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/353 kB of archives.
After this operation, 1,409 kB of additional disk space will be used.
dpkg: considering removing dcp130clpr:i386 in favour of brother-lpr-drivers-bh7 ...
dcp130clpr:i386 is not properly installed - ignoring any dependencies on it.
dpkg: package dcp130clpr:i386 requires reinstallation, will not remove.
dpkg: regarding .../brother-lpr-drivers-bh7_1.0.1-1-0ubuntu5_amd64.deb containing brother-lpr-drivers-bh7:
 brother-lpr-drivers-bh7 conflicts with dcp130clpr
  dcp130clpr:i386 (version 1.0.1-1) is present and broken due to failed removal or installation.
dpkg: error processing /var/cache/apt/archives/brother-lpr-drivers-bh7_1.0.1-1-0ubuntu5_amd64.deb (--unpack):
 conflicting packages - not installing brother-lpr-drivers-bh7
Errors were encountered while processing:
 /var/cache/apt/archives/brother-lpr-drivers-bh7_1.0.1-1-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


the output from sudo dpkg -C is as follows:

The following packages are in a mess due to serious problems during
installation. They must be reinstalled for them (and any packages
that depend on them) to function properly:
 dcp130clpr:i386      Brother lpr Inkjet Printer Definitions

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 brother-lpr-drivers-common Common files for brother-lpr-drivers packages
 brother-cups-wrapper-common Common files for Brother cups wrapper packages
 brother-cups-wrapper-bh7 Cups Wrapper drivers for bh7 brother printers

however i cant find a way to remove dcp130clpr:i386 so i can install  brother-cups-wrapper-bh7 which is needed to operate the printer correctly

can any one help??

---

