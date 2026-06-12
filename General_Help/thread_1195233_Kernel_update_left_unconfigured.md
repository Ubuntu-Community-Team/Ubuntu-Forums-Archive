---
title: "Kernel update left unconfigured"
date: 2009-06-23
forum: General Help
---

### Post by Zyrshnikashnu on 2009-06-23
I was unable to apply yesterday's kernel update to 2.6.28.13. apt gives me the following errors:

```
The following partially installed packages will be configured:
  linux-generic linux-image-2.6.28-13-generic linux-image-generic 
  linux-restricted-modules-2.6.28-13-generic 
  linux-restricted-modules-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.28-13-generic (2.6.28-13.44) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.28-13-generic)
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-generic:
 linux-restricted-modules-2.6.28-13-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-13-generic; however:
  Package linux-restricted-modules-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.13.17); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-restricted-modules-2.6.28-13-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.28-13-generic (2.6.28-13.44) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.28-13-generic)
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-generic:
 linux-restricted-modules-2.6.28-13-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-13-generic; however:
  Package linux-restricted-modules-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.13.17); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-restricted-modules-2.6.28-13-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

```

I noticed that the first dependency problem on the list was caused because linux-image-2.6.28-13-generic was unconfigured. First I tried reinstalling it, which prompted this error (part of the above errors):

```
Setting up linux-image-2.6.28-13-generic (2.6.28-13.44) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.28-13-generic)
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
```

So I tried removing it with apt-get. Same problem. This is looking like dependency hell.


For reference:
sources.list:
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirrors.rit.edu/ubuntu/ jaunty main restricted
deb-src http://mirrors.rit.edu/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.rit.edu/ubuntu/ jaunty-updates main restricted
deb-src http://mirrors.rit.edu/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.rit.edu/ubuntu/ jaunty universe
deb-src http://mirrors.rit.edu/ubuntu/ jaunty universe
deb http://mirrors.rit.edu/ubuntu/ jaunty-updates universe
deb-src http://mirrors.rit.edu/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.rit.edu/ubuntu/ jaunty multiverse
deb-src http://mirrors.rit.edu/ubuntu/ jaunty multiverse
deb http://mirrors.rit.edu/ubuntu/ jaunty-updates multiverse
deb-src http://mirrors.rit.edu/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://mirrors.rit.edu/ubuntu/ jaunty-security main restricted
deb-src http://mirrors.rit.edu/ubuntu/ jaunty-security main restricted
deb http://mirrors.rit.edu/ubuntu/ jaunty-security universe
deb-src http://mirrors.rit.edu/ubuntu/ jaunty-security universe
deb http://mirrors.rit.edu/ubuntu/ jaunty-security multiverse
deb-src http://mirrors.rit.edu/ubuntu/ jaunty-security multiverse
deb http://apt.wicd.net jaunty extras
```

uname -a:
```
Linux Odessa 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```

---

### Post by DeMus on 2009-06-23
I recently installed 2.6.30 using *.deb files. Very easy to do:
Look [here]("http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/"):

and use the instructions on that page.

---

### Post by Zyrshnikashnu on 2009-06-23
I actually tried that a few days ago, but my graphics driver was incompatible. I suppose I could just download the latest from Nvidia's website.

---

### Post by DeMus on 2009-06-24
> **Zyrshnikashnu said:**
> I actually tried that a few days ago, but my graphics driver was incompatible. I suppose I could just download the latest from Nvidia's website.

Yes, well I think you can do that. I just wonder why it doesn't work for you. I worked fine here, every time I did it. The nVidia driver was included into the new kernel and works as it should.
Which driver do you use?

---

