---
title: "pbuilder create problem"
date: 2006-04-26
forum: Desktop Environments
---

### Post by MichaelZ on 2006-04-26
Hello,

I have a problem installing pbuilder correctly. I have followed the instructions reported in [https://wiki.ubuntu.com/PbuilderHowto]("https://wiki.ubuntu.com/PbuilderHowto") and download pbuilder, but when I try:

> 
sudo pbuilder create --distribution breezy
 
I get an error:

> 
I: Base system installed successfully.
 -> debootstrap finished
 -> copying local configuration
  -> Installing apt-lines
-> Copy /etc/pbuilder/apt.config//apt.conf.d /etc/pbuilder/apt.config//secring.gpg /etc/pbuilder/apt.config//sources.list /etc/pbuilder/apt.config//sources.list.save /etc/pbuilder/apt.config//trustdb.gpg /etc/pbuilder/apt.config//trusted.gpg /etc/pbuilder/apt.config//trusted.gpg~ to chroot
Refreshing the base.tgz
 -> upgrading packages
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
 -> installing dummy policy-rc.d
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy ReleaseIgn cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy Release [30.9kB]
Get:6 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security Release [27.0kB]
Get:7 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates Release [30.9kB]
Get:8 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports Release [19.6kB]
Get:9 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/main Packages [585kB]
Get:10 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Packages [47.6kB]
Get:11 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Packages [4458B]
Get:12 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Sources [15.1kB]
Get:13 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Sources [960B]
Get:14 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/universe Packages [33.5kB]
Get:15 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/universe Sources [5007B]
Get:16 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/restricted Packages [5061B]
Get:17 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/main Sources [232kB]
Get:18 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/restricted Sources [1454B]
Get:19 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/universe Packages [2304kB]
Get:20 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/universe Sources [915kB]
Get:21 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates/main Packages [39.0kB]
Get:22 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates/restricted Packages [14B]
Get:23 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates/main Sources [18.6kB]
Get:24 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates/restricted Sources [14B]
Get:25 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/main Packages [14.0kB]
Get:26 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/restricted Packages [14B]
Get:27 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/universe Packages [26.1kB]
Get:28 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/multiverse Packages [1353B]Get:29 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/main Sources [5185B]
Get:30 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/restricted Sources [14B]
Get:31 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/universe Sources [10.2kB]
Get:32 [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-backports/multiverse Sources [701B]
Fetched 4374kB in 14s (299kB/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
 -> Aborting with an error
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env
    -> removing directory /var/cache/pbuilder/build//2508 and its subdirectories
 

I have tried to remove the CD, to do sudo apt-cdrom add, but nothing seems to work.

Thank you very much.

Best wishes,
Michael

---

