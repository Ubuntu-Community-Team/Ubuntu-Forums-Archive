---
title: "What the heck does this mean?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by denzilla on 2005-04-22
I commented out the bottom repos because they were wanting to DL some updates that weren't for ubuntu. After sudo apt-get update, I get this now:

Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backport](http://backports.ubuntuforums.org/backports/dists/hoary-backport) s/main/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backport](http://backports.ubuntuforums.org/backports/dists/hoary-backport) s/universe/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backport](http://backports.ubuntuforums.org/backports/dists/hoary-backport) s/multiverse/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backport](http://backports.ubuntuforums.org/backports/dists/hoary-backport) s/restricted/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/m](http://backports.ubuntuforums.org/backports/dists/hoary-extras/m) ain/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/u](http://backports.ubuntuforums.org/backports/dists/hoary-extras/u) niverse/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/m](http://backports.ubuntuforums.org/backports/dists/hoary-extras/m) ultiverse/binary-i386/Packages.gz  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/r](http://backports.ubuntuforums.org/backports/dists/hoary-extras/r) estricted/binary-i386/Packages.gz  500 Internal Server Error
Reading package lists... Done
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_di sts_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directo ry)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backport s_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or  directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-bac kports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backpo rts_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fil e or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists _hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_d ists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or direc tory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-ext ras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports _dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or d irectory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.


[COLOR=Red]Here is my repos file as it is now:
[/COLOR]

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main


Any idea whats wrong?

Thanks

---

### Post by alastair on 2005-04-22
A wild guess would be a problem with the server "backports.ubuntuforums.org", so I would try again later (or tomorrow).

---

### Post by denzilla on 2005-04-22
I figured it was a problem on their end because I disabled them last night while I was messing around and never had any issues with sudo apt-get update.

Thanks

---

