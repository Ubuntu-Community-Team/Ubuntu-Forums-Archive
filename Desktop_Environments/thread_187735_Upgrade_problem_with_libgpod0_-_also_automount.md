---
title: "Upgrade problem with libgpod0 - also automount"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-06-03
After several attempts, I know seem to have got my Dapper upgrade working.

There's a few things still wrong - most notably I can't automount my iPod.

Following the upgrade, plus running apt-get -f install. there seems to be one remaining package problem - with **libgpod0.**  Here's what I'm getting:

```

myusername@cpc1-eswd2-4-1-cust78:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libgpod0
Recommended packages:
  libgpod-common
The following NEW packages will be installed
  libgpod0
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
158 not fully installed or removed.
Need to get 0B/64.2kB of archives.
After unpacking 188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 95162 files and directories currently installed.)
Unpacking libgpod0 (from .../libgpod0_0.3.2-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgpod.so.0', which is also in package libgpod
Errors were encountered while processing:
 /var/cache/apt/archives/libgpod0_0.3.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

A lot of packages seem to be dependent on libgpod0.

Could this also have something to do with my automount problem?

Can someone remind me how to mount my iPod manually?

Ta

---

