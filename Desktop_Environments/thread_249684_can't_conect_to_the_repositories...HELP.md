---
title: "can't conect to the repositories...HELP"
date: 2006-09-02
forum: Desktop Environments
---

### Post by johnficca on 2006-09-02
I type apt-get update and I get this:

johnficca@johnficca-desktop:~$ sudo apt-get update
Password:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Connection failed [IP: 195.248.90.54 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Connection failed
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz)  Connection failed
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
johnficca@johnficca-desktop:~$

I don't know what to do please help

---

