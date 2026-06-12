---
title: "What does this mean?"
date: 2006-04-20
forum: Desktop Environments
---

### Post by thulanism on 2006-04-20
Every time i try to install from the command line. i see this message:

W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package zlib

Please help...

---

### Post by jazzmuzik on 2006-04-20
Looks like you are not connecting to the repositories. Are you online when doing this? Are you prepending your command with sudo?

---

### Post by thulanism on 2006-04-20
Yes, I am online, and yes I do put sudo before the command, 

e.g: thulani@thulani# sudo apt-get install zlib

To make things worse, when I try to update apt-get, this is whay I get:

root@thulani:/home/thulani# sudo apt-get update
44% [Connecting to archive.ubuntu.com (85.133.25.7)] [Connecting to security.ub

It gets stuck at this point until it says "Connection timed out"

What's wrong...

---

### Post by art on 2006-04-20
I think it is your /etc/apt/sources.list that is misconfigured. Did you try changing the servers in it and do sudo apt-get update after that?

---

### Post by louis_nichols on 2006-04-21
perhaps you are using a proxy. you have the option to set the proxy for apt-get update in synaptic, under settings.

---

