---
title: "Upgrade breaking kdelibs-data"
date: 2005-04-26
forum: Desktop Environments
---

### Post by localzuk on 2005-04-26
When i run a apt-get upgrade dist-upgrade (after running apt-get update) I get the following error:
```

root@goldfish:/home/ayrea # apt-get dist-upgrade upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.

```

Then when I follow its advice and try apt-get -f install, I get this:

```

root@goldfish:/home/ayrea # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
21 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 116967 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What do I need to do in order to fix this? It is obviously linked to 'knetworkconf' but how do I get around this?

---

### Post by lao_V on 2005-04-26
A lot of people have got around this, including myself, by uninstalling knetworkconf first and then updating kdelibs-data and then re-installing knetworkconf..

---

### Post by localzuk on 2005-04-26
running a 'sudo apt-get remove knetworkconf' doesn't remove it - instead it complains with:

```

root@goldfish:/home/ayrea # apt-get -f remove knetworkconf
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.1) but 4:3.4.0-0ubuntu3 is to be installed
  kubuntu-desktop: Depends: knetworkconf but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

```

---

