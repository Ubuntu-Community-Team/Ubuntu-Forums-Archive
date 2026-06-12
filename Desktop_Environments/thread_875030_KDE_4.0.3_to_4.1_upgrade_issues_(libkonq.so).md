---
title: "KDE 4.0.3 to 4.1 upgrade issues (libkonq.so)"
date: 2008-07-30
forum: Desktop Environments
---

### Post by mondo1287 on 2008-07-30
I'm trying to upgrade from KDE 4.0.3 to 4.1 and I'm running Kubuntu Hardy.  I've done apt-get dist-upgrade which did not fully complete.  I was then prompted to run apt-get -f install which produces:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 libstdc++5-3.3-dev g++-3.3 libboost-dev libaccess-bridge-java libkrosspython0 openjdk-6-jre-headless tzdata-java openjdk-6-jre-lib
  linux-headers-2.6.24-18-generic libkrossruby0 libzip1 kmilo-kde4 linux-headers-2.6.24-18 kjots-kde4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 libkonq5-dev libplasma2 sweeper-kde4
Suggested packages:
  kdebase-workspace-wallpapers
The following packages will be REMOVED:
  libplasma1
The following NEW packages will be installed:
  kdebase-workspace-libs4+5 libplasma2
The following packages will be upgraded:
  kdebase-workspace-bin kdebase-workspace-data libkonq5-dev sweeper-kde4
4 upgraded, 2 newly installed, 1 to remove and 123 not upgraded.
57 not fully installed or removed.
Need to get 0B/10.0MB of archives.
After this operation, 4698kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libkonq5-dev kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 libplasma2 sweeper-kde4
Install these packages without verification [y/N]? y
(Reading database ... 187302 files and directories currently installed.)
Preparing to replace libkonq5-dev 4:4.0.3-0ubuntu2 (using .../libkonq5-dev_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb) ...
Unpacking replacement libkonq5-dev ...
dpkg: error processing /var/cache/apt/archives/libkonq5-dev_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/libkonq.so', which is also in package kdebase-dev-kde4
Errors were encountered while processing:
 /var/cache/apt/archives/libkonq5-dev_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks!

---

### Post by Ataris on 2008-07-30
To get KDE 4 I think you (STILL!) have to use ```
sudo apt-get install kubuntu-kde4-desktop
``` and treat it like another desktop environment. I have KDE 4 and 3 right now. Also, KDE 3 programs don't always work on KDE 4. Right now KDE 4 isn't the best, and I would be hesitant to use it unless you like the new features and won't be doing too sophisticated work on it.

---

### Post by mondo1287 on 2008-07-31
Thanks, but at this point I can't do anything because:

> apt-get install kubuntu-kde4-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdebase-plasma-kde4: Depends: libplasma2 but it is not going to be installed
  kdeutils-kde4: Depends: sweeper-kde4 (>= 4:4.1.0-0ubuntu1~hardy1~ppa2) but 4:4.0.3-0ubuntu4 is to be installed
  kget-kde4: Depends: libplasma2 but it is not going to be installed
  knewsticker-kde4: Depends: libplasma2 but it is not going to be installed
  ksysguard-kde4: Depends: kdebase-workspace-libs4+5 but it is not going to be installed
                  Depends: libplasma2 but it is not going to be installed
  kubuntu-kde4-desktop: Depends: kde-window-manager but it is not going to be installed
                        Depends: khelpcenter-kde4 but it is not going to be installed
                        Recommends: dragonplayer but it is not going to be installed
                        Recommends: im-switch but it is not going to be installed
                        Recommends: kdesudo-kde4 but it is not going to be installed
                        Recommends: oxygen-cursor-theme but it is not going to be installed
  libkonq5-dev: Depends: libkonq5 (= 4:4.0.3-0ubuntu2) but 4:4.1.0-0ubuntu1~hardy1~ppa2 is to be installed
  libplasma-dev: Depends: libplasma2 (>= 4:4.1.0-0ubuntu1~hardy1~ppa1) but it is not going to be installed
  superkaramba-kde4: Depends: libplasma2 but it is not going to be installed
E: Unmet dependencies. Try **'apt-get -f install'** with no packages (or specify a solution).

---

### Post by mortenb on 2008-08-01
For some reason it did the same for me until I used the adept package manager.

---

### Post by mondo1287 on 2008-08-01
Adept didn't work for me either, it kept saying there were errors applying changes.  I ended up purging libkonq5-dev, then dpkg --configure -a, then apt-get upgrade and all seems well.

---

### Post by Phill Kenoyer on 2008-08-04
Finally got mine to work.  I typed in "aptitude install" and it magically fixed it.

---

### Post by hemna on 2008-08-04
How did you purge the package?  I can't seem to get apt to do anything now due to this issue.


> root@wboring:/mnt/p_drive$ apt-get purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libkonq5-dev: Depends: libkonq5 (= 4:4.0.3-0ubuntu2) but 4:4.1.0-0ubuntu1~hardy1~ppa2 is installed
E: Unmet dependencies. Try using -f.

> 
root@wboring:/mnt/p_drive$ apt-get purge -f libkonq5-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kde4-devel: Depends: libkonq5-dev (>= 4:4.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



> root@wboring:/mnt/p_drive$ apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libkonq5-dev
The following packages will be upgraded:
  libkonq5-dev
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
9 not fully installed or removed.
Need to get 0B/25.7kB of archives.
After this operation, 16.4kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libkonq5-dev
Install these packages without verification [y/N]? y
(Reading database ... 288206 files and directories currently installed.)
Preparing to replace libkonq5-dev 4:4.0.3-0ubuntu2 (using .../libkonq5-dev_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb) ...
Unpacking replacement libkonq5-dev ...
dpkg: error processing /var/cache/apt/archives/libkonq5-dev_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/libkonq.so', which is also in package kdebase-dev-kde4
Errors were encountered while processing:
 /var/cache/apt/archives/libkonq5-dev_4%3a4.1.0-0ubuntu1~hardy1~ppa2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

