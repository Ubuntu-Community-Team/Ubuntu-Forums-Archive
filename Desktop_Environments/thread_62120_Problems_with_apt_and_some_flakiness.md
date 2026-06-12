---
title: "Problems with apt and some flakiness"
date: 2005-09-03
forum: Desktop Environments
---

### Post by cdubks88 on 2005-09-03
Ubuntu 5.0.4 i386 on a PII 300 with 192MB

Install went fine, but after I tried to get several packages installed (the software updater came up and wanted to run, so I let it do it's thing, and I got errors from apt saying not all the packages could be updated).

The errors suggested doing an apt-get update or apt-get upgrade or apt-get dist-upgrade (I think that last one is right....).

Anyway, the system won't let me install a lot of stuff because of general errors with dependencies, but when I go to install the dependencies, then it belly aches about the ones that I tried to previously install.....

I'm a tad frustrated at this point and if I can't resolve this soon, I'm going to have to go to another distro.

I don't particularly want to, but I've got to have something that just works.

Any ideas?

Thanks in advance, 

C.

---

### Post by cdubks88 on 2005-09-03
Here's what I get when I do an apt-get upgrade:

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  hal: Depends: udev (>= 0.063) but 0.050-3ubuntu7 is installed
E: Unmet dependencies. Try using -f.

Here's what I got from apt-get -f install:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  udev
The following packages will be upgraded:
  udev
1 upgraded, 0 newly installed, 0 to remove and 228 not upgraded.
389 not fully installed or removed.
Need to get 0B/310kB of archives.
After unpacking 258kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  udev
Install these packages without verification [y/N]? y
(Reading database ... 66882 files and directories currently installed.)
Preparing to replace udev 0.050-3ubuntu7 (using .../archives/udev_0.068-2_i386.deb) ...
ln: `/etc/udev/rules.d/020_permissions.rules': File exists
dpkg: error processing /var/cache/apt/archives/udev_0.068-2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/udev_0.068-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

