---
title: "Something odd with my &quot;get-apt&quot; command..."
date: 2005-05-01
forum: Desktop Environments
---

### Post by Zensunni on 2005-05-01
Okay, for me and for many others, this is their first real experience with linux. I've had hardcore windows experience (except for actual document modification...witch is always frowned upon in ms).

Anyways, I'm having trouble on the "apt-get" command. I went to the "ubuntuguide.org" and have tried to make a few updates. However, when I try things like dvd playback and media codecs, I get errors at the end of the process. I've run the "sudo get-apt update" but I get this:

Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release .gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Pa ckages
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restric ted Packages
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Pa ckages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restric ted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:6 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages [20B]
Get:7 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages [20B]
Get:8 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages [20B ]
Get:9 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages [20B ]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Get:10 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages [20B]
Get:11 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages [20B]
Get:12 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages [20B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Get:13 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages [20B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release
Get:14 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release [1349B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Fetched 18.6kB in 3s (5782B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/d ists/hoary/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-R OM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/d ists/hoary/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make thi s CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable  to find expected entry  main/binary-amd64/Packages in Meta-index file (malforme d Release file?)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/Release](ftp://ftp.nerim.net/debian-marillat/dists/testing/Release)  Unabl e to find expected entry  main/binary-amd64/Packages in Meta-index file (malform ed Release file?)
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Rele ase i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fH oary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-amd 64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Rele ase i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04% 20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricte d_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/ var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_P ackages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages ( /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64 _Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Rele ase i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fH oary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-amd 64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Rele ase i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04% 20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricte d_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/ var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_P ackages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages ( /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64 _Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

If you want to see what I get when I try various installs, i'll show you for reference...BTW, i'm a fish out of water here, so you'll have to walk me through like a little kid.

---

### Post by Nis on 2005-05-03
First, I would suggest not using nerim.net.  It is a repository made for Debian and mixing Ubuntu repositories with Debian repositories can lead to problems later on.  If you want to get rid of these messages open up /etc/apt/sources.list with sudo.
```

sudo gedit /etc/apt/sources.list

```
Comment out any lines pretaining to a CD-ROM and then
```

sudo apt-get update

```

If you want libdvdcss and w32codecs then try the [Ubuntu backports project](backports.ubuntuforums.org).  These and many other packages are hosted here and are built against Hoary.

---

