---
title: "Synaptic &amp; apt-get problems..."
date: 2006-03-07
forum: Desktop Environments
---

### Post by Swiss on 2006-03-07
Whenever I go to install anything via apt or syn, I get this:

```

jack@Ubuntu:~$ sudo apt-get update
Err http://kubuntu.org breezy Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://koti.mbnet.fi breezy/ Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign http://kubuntu.org breezy Release
Ign http://koti.mbnet.fi breezy/ Release
Err http://deb.opera.com etch Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign http://kubuntu.org breezy/main Packages
Ign http://koti.mbnet.fi breezy/ Packages
Ign http://deb.opera.com etch Release
Err http://kubuntu.org breezy/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign http://koti.mbnet.fi breezy/ Sources
Ign http://deb.opera.com etch/non-free Packages
Err http://koti.mbnet.fi breezy/ Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://deb.opera.com etch/non-free Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://koti.mbnet.fi breezy/ Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://wine.sourceforge.net binary/ Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign http://wine.sourceforge.net binary/ Release
Ign http://wine.sourceforge.net binary/ Packages
Err http://wine.sourceforge.net binary/ Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Err http://security.ubuntu.com breezy-security/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/universe Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/universe Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Ign http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy-updates Release
Ign http://archive.ubuntu.com breezy-backports Release
Ign http://archive.ubuntu.com breezy/main Sources
Ign http://archive.ubuntu.com breezy/restricted Sources
Ign http://archive.ubuntu.com breezy/universe Sources
Ign http://archive.ubuntu.com breezy/universe Packages
Ign http://archive.ubuntu.com breezy/main Packages
Ign http://archive.ubuntu.com breezy/restricted Packages
Ign http://archive.ubuntu.com breezy/multiverse Packages
Ign http://archive.ubuntu.com breezy-updates/main Packages
Ign http://archive.ubuntu.com breezy-updates/restricted Packages
Ign http://archive.ubuntu.com breezy-updates/main Sources
Ign http://archive.ubuntu.com breezy-updates/restricted Sources
Ign http://archive.ubuntu.com breezy-backports/main Packages
Ign http://archive.ubuntu.com breezy-backports/restricted Packages
Ign http://archive.ubuntu.com breezy-backports/universe Packages
Ign http://archive.ubuntu.com breezy-backports/multiverse Packages
Err http://archive.ubuntu.com breezy/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/universe Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/universe Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy/multiverse Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/main Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-updates/restricted Sources
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-backports/main Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-backports/restricted Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-backports/universe Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com breezy-backports/multiverse Packages
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Get:1 ftp://ftp.free.fr breezy Release.gpg
Ign ftp://ftp.free.fr breezy Release.gpg
Get:2 ftp://ftp.free.fr breezy Release
Ign ftp://ftp.free.fr breezy Release
Get:3 ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Packages
Get:4 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:5 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:6 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://wine.sourceforge.net/apt/binary/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://deb.opera.com/opera/dists/etch/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://kubuntu.org/packages/kde351/dists/breezy/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Release.gpg  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://wine.sourceforge.net/apt/binary/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Xian on 2006-03-07
Is this an issue that has just appeared?? I mean to say I take it you haven't recently changed your sources list, ISP, machine hame, hosts file, firewall, router, modem, iptables, or any other such device or software...

---

### Post by Ramses de Norre on 2006-03-07
Your internet connection is configured wrong, it's trying to acces http through the lo connection which is the loopback..

---

### Post by Swiss on 2006-03-07
I added a firewall... And SSH.

I can browse the net fine...

---

### Post by Ramses de Norre on 2006-03-12
```
Could not connect to localhost:80 (127.0.0.1)
```
Apt is trying to connect to a http server (port 80) through lo (127.0.0.1) instead of your ethernet card (eth0?).
Does it work with the firewall turned off?
I have no idea were to correct this..

---

