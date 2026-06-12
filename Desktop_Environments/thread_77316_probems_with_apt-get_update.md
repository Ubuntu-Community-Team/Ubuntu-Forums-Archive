---
title: "probems with apt-get update"
date: 2005-10-16
forum: Desktop Environments
---

### Post by brian31 on 2005-10-16
Everytime I run apt-get update I keep getting this error.
```

Get:1 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ign http://us.archive.ubuntu.com breezy-backports Release.gpg
Hit http://us.archive.ubuntu.com breezy Release
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy-backports Release
Hit http://us.archive.ubuntu.com breezy/main Packages
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy/main Sources
Hit http://us.archive.ubuntu.com breezy/restricted Sources
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/universe Sources
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://us.archive.ubuntu.com breezy-updates/main Sources
Hit http://us.archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found [IP: 82.211.81.167 80]
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found [IP: 82.211.81.167 80]
Fetched 20.0kB in 1s (12.3kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  404 Not Found [IP: 82.211.81.167 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  404 Not Found [IP: 82.211.81.167 80]
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I can see it tells me to run apt-get update but it clearly does not help.
Anyone know how to fix this?
thanks

---

### Post by Ampersand on 2005-10-16
There aren't any breezy backports available yet. They'll probably be added after the Dapper features freeze in a few months, until then they can be removed from your sources list.

---

### Post by souled on 2005-10-16
The backports are going to be opened when the DD development opens, which is going to be Tuesday the 18th.

---

