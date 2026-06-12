---
title: "Multiverse crapping out on me"
date: 2005-11-12
forum: Desktop Environments
---

### Post by jimmygoon on 2005-11-12
```
jimmygoon@ubuntu-laptop:~$ sudo gedit /etc/apt/sources.list
Password:
jimmygoon@ubuntu-laptop:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Ign http://dl.sourceforge.net ./ Release.gpg
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://dl.sourceforge.net ./ Release
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ign http://dl.sourceforge.net ./ Packages
Hit http://security.ubuntu.com breezy-security Release
Ign http://dl.sourceforge.net ./ Sources
Hit http://dl.sourceforge.net ./ Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Hit http://dl.sourceforge.net ./ Sources
Hit http://us.archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports Release
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found
Fetched 3B in 4s (1B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
jimmygoon@ubuntu-laptop:~$ http://us.archive.ubuntu.com/ubuntu/


```

The first command was me enabling the multiverse (backports) as a repository.

Then I ran apt-get update and it pulls that on me.

WHY?!

btw: I wen to this folder: [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386) and it really is empy... there is no Package.gz.tar

what does this mean?

thanks ( all I want to do is install java :( and I need java-package)

---

### Post by Xian on 2005-11-12
[QUOTE=jimmygoon]what does this mean?[/QUOTE]
Edit your /etc/apt/sources.list file and change the backport mirrors to:

```
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

