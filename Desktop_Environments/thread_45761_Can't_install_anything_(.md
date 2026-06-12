---
title: "Can't install anything :("
date: 2005-07-01
forum: Desktop Environments
---

### Post by tekeo on 2005-07-01
Hello my system was doing great and I tried to install nv-clock (or something) when it gave me error messages (403 forbidden) then I decided to do 'sudo apt-get update'

when I get this error:
tekeo@ubuntu:~$ sudo apt-get update
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary Release
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates Release
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/main Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/restricted Packages
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/main Sources
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/restricted Sources
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/universe Packages
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/universe Sources
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/main Packages
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/restricted Packages
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/main Sources
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/main Packages
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/restricted Packages
  403 Forbidden [IP: 130.239.18.137 80]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/main Sources
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/restricted Sources
  403 Forbidden [IP: 130.239.18.137 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/universe Packages
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary/universe Sources
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/main Packages
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/restricted Packages
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/main Sources
  403 Forbidden [IP: 130.239.18.137 80]
Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hoary-updates/restricted Sources
  403 Forbidden [IP: 130.239.18.137 80]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Fetched 17.0kB in 3s (5625B/s)
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  403 Forbidden [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  403 Forbidden [IP: 130.239.18.137 80]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

it worked great 5 min ago when installing gimp but now...

Please help me!!!
//TeKeO

---

### Post by tekeo on 2005-07-01
I fixed it by copying a backup of it and then change all 'se' to 'dk' (denmark) and it worked. I guess something is wrong with the servers ;)

//TeKeO

---

