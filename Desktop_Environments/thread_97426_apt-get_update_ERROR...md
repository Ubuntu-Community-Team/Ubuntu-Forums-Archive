---
title: "apt-get update ERROR.."
date: 2005-12-01
forum: Desktop Environments
---

### Post by windowsXuser on 2005-12-01
of a sudden i was starting to get errors everytime i do an update..
Hopfully someone can help me out.

blair@kubuntu:~$ sudo apt-get update
Password:
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 5B in 2s (2B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Could not connect to packages.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


blair..

---

### Post by aysiu on 2005-12-01
I'm not sure what you need from PLF, but I know the sources.list I have (from the first link in my sig) is working. I just did this a few seconds ago ```
sudo apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 59.4kB in 3s (18.3kB/s)
Reading package lists... Done
```

---

