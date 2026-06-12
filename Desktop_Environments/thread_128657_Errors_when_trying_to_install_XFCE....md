---
title: "Errors when trying to install XFCE..."
date: 2006-02-12
forum: Desktop Environments
---

### Post by Leiki on 2006-02-12
I tried to install XFCE by running ```
sudo apt-get install xubuntu-desktop
``` and I get multiple error messages, but they look the same: ```
andrew@172:~$ sudo apt-get install xubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package xubuntu-desktop

``` So then I ran ```
sudo apt-get update
``` and even that gave me errors: ```
andrew@172:~$ sudo apt-get update
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Hit http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Get:3 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary Release
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  404 Not Found
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Get:4 http://security.ubuntu.com hoary-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://security.ubuntu.com hoary-security Release
Ign http://security.ubuntu.com hoary-security Release
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 192B in 17s (11B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://security.ubuntu.com hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
How can I fix this? Thank you.

P.S. - And does anyone know how I could install the Links browser?

---

### Post by aysiu on 2006-02-12
Mirrormax is dead. See the first link of my signature for more details.

The name of the browser you're looking for is *Lynx*, not *Links*.

---

### Post by Leiki on 2006-02-12
Thanks for your help! That did the trick. About Links: are we talking about the same thing? - [http://links.sourceforge.net/](http://links.sourceforge.net/)

---

