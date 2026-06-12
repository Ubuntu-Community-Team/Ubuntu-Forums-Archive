---
title: "Repositrie Problems"
date: 2006-05-25
forum: Desktop Environments
---

### Post by CameronCalver on 2006-05-25
hey i have been having troubles with my repositries and i need some help ok i went to check for updates in synaptic because update manager came up and told me i had updates so i clicked mark all updates and this is what happened it said it had 109 mb to download but as soon as it started it said configuring packages then this came up

Changes Applied

Failed to Apply all changes scroll the terminal buffer to see what went wrong

Terminal
Preconfiguring Packages........

---

### Post by Sef on 2006-05-25
Try this and see if you get a more detailed message, if so please copy and paste it here.

Open the Terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get upgrade

---

### Post by CameronCalver on 2006-05-26
this is it

calver@ubuntu:~$ sudo apt-get update
Password:
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [191B]
Get:4 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy/main Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy/main Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [60.6kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.5kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35.0kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages [12.9kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages [708B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Sources [1343B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Sources [365B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [3830B]Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [1025B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources [5185B]
Get:32 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources [10.2kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:36 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:37 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:38 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:39 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Fetched 337kB in 19s (17.6kB/s)
Reading package lists... Done
calver@ubuntu:~$
calver@ubuntu:~$
calver@ubuntu:~$
calver@ubuntu:~$
calver@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  kdelibs-bin kdelibs-data kdelibs4c2 ktuberling libarts1c2 libartsc0
  libavahi-client1 libavahi-common0 libavahi-qt3-0 libkdegames1 mplayer-386
  openoffice.org2 openoffice.org2-base openoffice.org2-calc
  openoffice.org2-common openoffice.org2-core openoffice.org2-draw
  openoffice.org2-evolution openoffice.org2-gnome
  openoffice.org2-help-en-us openoffice.org2-impress
  openoffice.org2-java-common openoffice.org2-l10n-en-us
  openoffice.org2-math openoffice.org2-writer python-uno ttf-opensymbol
  update-manager
28 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/109MB of archives.
After unpacking 3850kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  openoffice.org2-l10n-en-us openoffice.org2-core openoffice.org2-common
  ttf-opensymbol openoffice.org2-java-common python-uno
  openoffice.org2-writer openoffice.org2-calc openoffice.org2-draw
  openoffice.org2-impress openoffice.org2-math openoffice.org2-base
  openoffice.org2 openoffice.org2-evolution openoffice.org2-gnome
  openoffice.org2-help-en-us
Install these packages without verification [y/N]? y

Preconfiguring packages ...
dpkg: `ldconfig' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
calver@ubuntu:~$

---

### Post by CameronCalver on 2006-05-28
another thing when i try to uninstall anything it gives an error look at this 

calver@ubuntu:~$ sudo apt-get remove abuse
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  abuse abuse-frabs abuse-sdl abuse-sfx
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 16.3MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: `ldconfig' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
calver@ubuntu:~$

---

### Post by Ramses de Norre on 2006-05-28
```
sudo -i
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
aptitude update && aptitude upgrade
exit
```

Don't know why your PATH variable is wrong though.. This is a fix untill you reboot.

---

### Post by CameronCalver on 2006-05-29
hey dont worry bout it im just going to back up everything on my networked computer and then do i fresh install of breezy then upgrade to dapper on june 1

---

