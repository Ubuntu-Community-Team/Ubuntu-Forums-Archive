---
title: "apt-get upgrade failure"
date: 2009-01-09
forum: General Help
---

### Post by jlrubin on 2009-01-09
I am running xubuntu 8.04.1. I no longer use any of the X-windows stuff, and run exclusively from the command line.


I use apt-get to update and upgrade once a week. Today, the upgrade generated lots of messages. A typescript file is attached.

Here are the first few errors reported:
```

Preparing to replace util-linux 2.13.1-5ubuntu2 (using .../util-linux_2.13.1-5ubuntu3_i386.deb) ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.

```

How do I recover?

---

### Post by detroit/zero on 2009-01-09
I was having that problem the other day with a Gimp update, protobuf, and a few other things.

I was in the middle of following a tutorial for something else and one of the instructions was ```
sudo apt-get dist-upgrade
``` and all the previously-failed updates came through for me. Maybe that will work for you? I'm not clear on exactly what the dist-upgrade command is/does, so educate yourself before you try it.

_**EDIT:**_

This comes from *man apt-get*:```
dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```

---

### Post by jlrubin on 2009-01-09
Thanks for the suggestion, but sudo apt-get dist-upgrade did not resolve the problem. The errors (see attachment on my original post) are mostly the same.

---

### Post by detroit/zero on 2009-01-09
Sorry.. I guess I read through it too quick the first time.

Looks like you're trying to install some i386-based programs with a computer using an i486-based kernel.

Way out of my league. I had to look up what i486 even was.

Maybe someone else has an answer.

---

### Post by jlrubin on 2009-01-10
Bump

---

### Post by mgol on 2009-01-10
Have You installed any packages from outside the default repository? It looks like one of them changed the default errno entries to those related to the older kernel version.

---

### Post by namdung on 2009-01-10
Post output of 
```
sudo apt-get update
```
```
cat /etc/apt/sources.list
```

---

### Post by jlrubin on 2009-01-10
Output of "sudo apt-get update"

```

Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Reading package lists...

```

Contents of /etc/apt/sources.list:
**NOTE the last two lines.** I inserted them to install the transmission bit torrent client, and commented those lines out when I started to have this problem.


```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe restricted main multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# transmission bittorrent client
#deb http://ppa.launchpad.net/transmissionbt/ubuntu hardy main
#deb-src http://ppa.launchpad.net/transmissionbt/ubuntu hardy main


```

---

### Post by jlrubin on 2009-01-10
Yes, the transmission bit-torrent client. See a later post.

---

### Post by namdung on 2009-01-10
Pls clean ur sources.list file and remove all Gutsy entries. The entries looks fine and remove the transmission entry too.

Post output of```

sudo dpgk --configure -a
sudo apt-get autoremove
sudo apt-get upgrade
```

---

### Post by jlrubin on 2009-01-10
I will try this and post the results in a few hours. Thanks for your help.

---

### Post by jlrubin on 2009-01-12
Sorry to take so long to get back to you.

sudo dpg  --configure -a

```

dpkg: error processing util-linux (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 util-linux

```

sudo apt-get autoremove

```
The following extra packages will be installed:
  util-linux
The following packages will be upgraded:
  util-linux
1 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0B/440kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y


(Reading database ... 151813 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu2 (using .../util-linux_2.13.1-5ubuntu3_i386.deb) ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: warning - old pre-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 9
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

sudo apt-get upgrade


```

The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisccc30 libisccfg30 linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  bsdutils cupsys-bsd cupsys-client cupsys-common libcupsimage2 libcupsys2 liblwres30 libnm-glib0 libnm-util0
  libssl0.9.8 linux-libc-dev linux-restricted-modules-common network-manager ntp ntp-doc openssl util-linux
  util-linux-locales xterm
19 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B/8049kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y


Preconfiguring packages ...
(Reading database ... 151813 files and directories currently installed.)
Preparing to replace util-linux 2.13.1-5ubuntu2 (using .../util-linux_2.13.1-5ubuntu3_i386.deb) ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: warning - old pre-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error processing /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 9
Errno architecture (i486-linux-gnu-thread-multi-2.6.15.7) does not match executable architecture (i486-linux-gnu-thread-multi-2.6.24-14-server) at /usr/local/share/perl/5.8.8/Errno.pm line 11.
Compilation failed in require at /usr/sbin/install-info line 304.
BEGIN failed--compilation aborted at /usr/sbin/install-info line 304.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/util-linux_2.13.1-5ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dhuber on 2009-01-15
Hi, had the same problem.

open:

```
$> nano /usr/lib/perl/5.8.8/Config.pm
```

and find the string "osvers".

change it from "2.6.24-14-server" to "2.6.15.7"

now run apt-get upgrade and it should work.

---

### Post by jlrubin on 2009-01-15
Thanks, that solved the problem.

---

