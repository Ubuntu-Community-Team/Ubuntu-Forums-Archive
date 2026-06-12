---
title: "Installing Warsow has broken my apt-get"
date: 2011-04-28
forum: Gaming &amp; Leisure
---

### Post by wardrich on 2011-04-28
> installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 136799 files and directories currently installed.)

Unpacking warsow-data (from .../warsow-data_0.50+dfsg1-1_all.deb) ...

dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'

dpkg-deb: error: subprocess <decompress> returned error exit status 2

dpkg: error processing /var/cache/apt/archives/warsow-data_0.50+dfsg1-1_all.deb (--unpack):

 subprocess dpkg-deb --fsys-tarfile returned error exit status 2

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 /var/cache/apt/archives/warsow-data_0.50+dfsg1-1_all.deb

dpkg: dependency problems prevent configuration of warsow:

 warsow depends on warsow-data (>= 0.50); however:

  Package warsow-data is not installed.

dpkg: error processing warsow (--configure):

 dependency problems - leaving unconfigured



Looking for some advice on what to do, this was installed from the Software Center.
-This was on a fresh install of Ubuntu 11
-sudo apt-get -f install won't fix the problem.

---

### Post by SmilePiper on 2011-04-28
try installing the warsow-data and then try install warsow again.  On my Ubuntu 10.10 I installed the warsow-data by typing the followng:

sudo apt-get install warsow-data

---

### Post by wardrich on 2011-04-29
Thanks!  Seems to have freed it all up.  I'm still bordering on a re-install.  Linux never seems to like my computers :(  I have to ctrl-alt F1 and "Exit" the initramfs just to boot into a graphical desktop. lol.  I guess those are just the walls to expect when installing a beta release.

---

