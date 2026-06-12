---
title: "Is there a repository server down or something?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by equal on 2006-01-31
Both of my computers are suddenly giving me the same error when I try to apt-get install anything, and even sudo apt-get remove tells me to try doing an apt-get update. Here's the error I'm getting:

```

phil@ubuntu:~$ sudo apt-get update
Password:
Ign http://wine.sourceforge.net binary/ Release.gpg
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ign http://deb.opera.com etch Release.gpg
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Ign http://deb.opera.com etch Release
Ign http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Get:5 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://wine.sourceforge.net binary/ Release
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Ign http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Err http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
  404 Not Found
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Err http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
  404 Not Found
Get:8 ftp://ftp.free.fr breezy Release.gpg
Ign http://wine.sourceforge.net binary/ Packages
Ign ftp://ftp.free.fr breezy Release.gpg
Hit http://wine.sourceforge.net binary/ Packages
Ign http://deb.opera.com etch/non-free Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Get:9 ftp://ftp.free.fr breezy Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://deb.opera.com etch/non-free Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Ign ftp://ftp.free.fr breezy Release
Get:10 ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Packages
Get:11 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:12 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:13 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Fetched 59.4kB in 10s (5889B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
phil@ubuntu:~$

```

---

### Post by shade11 on 2006-01-31
Please post your /etc/apt/sources.list

---

### Post by RAOF on 2006-01-31
Yes.  The mirrormax repositories have shut down.  Remove the corresponing lines from your sources.list

---

### Post by equal on 2006-01-31
Ahh muchas gracias my friend :) much better now.

---

