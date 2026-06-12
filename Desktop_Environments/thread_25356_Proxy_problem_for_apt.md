---
title: "Proxy problem for apt"
date: 2005-04-09
forum: Desktop Environments
---

### Post by h3ndric on 2005-04-09
Hi, there.

My internet supposed to access thru a proxy. And i've set my proxy in the .bashrc 
export http_proxy="whatever:port"
export ftp_proxy="whatever:port"
export RSYNC_proxy="whatever:port"
And i try wget [www.yahoo.com](www.yahoo.com), it works, that means my proxy connection is correct. But when I try to use my apt-get, this is the log message that I got:
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary Release.gpg
  Could not resolve '8080'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates Release.gpg
  Could not resolve '8080'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  Could not resolve '8080'
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  Could not resolve '8080'
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
  Could not resolve '8080'
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
  Could not resolve '8080'
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/restricted Packages
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  Could not resolve '8080'
Ign [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/main Packages
  Could not resolve '8080'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/restricted Packages
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/main Sources
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/restricted Sources
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/universe Packages
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/universe Sources
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/main Packages
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/restricted Packages
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/main Sources
  Could not resolve '8080'
Err [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/restricted Sources
  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg](http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg)  Could not resolve '8080'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg)  Could not resolve '8080'
Failed to fetch cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  Could not resolve '8080'
Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://sg.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  Could not resolve '8080'
Reading package lists... Done
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Anybody has idea to solve this thing ?
Thanks

---

### Post by sjalex on 2005-04-10
> My internet supposed to access thru a proxy. And i've set my proxy in the .bashrc 
 export http_proxy="whatever:port"
 export ftp_proxy="whatever:port"
 export RSYNC_proxy="whatever:port"

You have to do
 export http_proxy="http://whatever:port/"
 export ftp_proxy="ftp://whatever:port/"
 export RSYNC_proxy="rsync://whatever:port/"

rsync won't work as an apt-get method without a /usr/lib/apt/methods/rsync driver though

---

