---
title: "Apt error"
date: 2006-01-21
forum: Desktop Environments
---

### Post by joselin on 2006-01-21
Hi,

Since a week or so, i couln't apt-get update from two of my three computers. The other work fine (as usually). In all off them the sources.list file have the same content.

We have no proxy and no firewall.

This is the output of the apt in the computer that can't receive info:

```

$ sudo apt-get update
Password:
Err http://antesis.freecontrib.org breezy Release.gpg
  Temporary failure resolving 'antesis.freecontrib.org'
Err http://download.gna.org ./ Release.gpg
  Temporary failure resolving 'download.gna.org'
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err http://es.archive.ubuntu.com breezy Release.gpg
  Could not connect to es.archive.ubuntu.com:80 (82.211.81.182), connection timed out
Err http://es.archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to es.archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch http://es.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Could not connect to es.archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch http://es.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Could not connect to es.archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Failed to fetch http://download.gna.org/gcfilms/ubuntu/./Release.gpg  Temporary failure resolving 'download.gna.org'
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg  Temporary failure resolving 'antesis.freecontrib.org'
Reading package lists... Done
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://es.archive.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/es.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.gna.org ./ Packages (/var/lib/apt/lists/download.gna.org_gcfilms_ubuntu_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

And this is the output of the one who works fine:

```

$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://es.archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:4 http://es.archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://es.archive.ubuntu.com breezy Release
Get:5 http://es.archive.ubuntu.com breezy-updates Release [19.6kB]
Get:6 http://security.ubuntu.com breezy-security/main Packages [32.9kB]
Get:7 http://es.archive.ubuntu.com breezy/main Packages [586kB]
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Get:8 http://security.ubuntu.com breezy-security/main Sources [10.2kB]
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://es.archive.ubuntu.com breezy/restricted Packages
Hit http://es.archive.ubuntu.com breezy/universe Packages
Hit http://es.archive.ubuntu.com breezy/multiverse Packages
Hit http://es.archive.ubuntu.com breezy/main Sources
Hit http://es.archive.ubuntu.com breezy/restricted Sources
Hit http://es.archive.ubuntu.com breezy/universe Sources
Hit http://es.archive.ubuntu.com breezy/multiverse Sources
Hit http://es.archive.ubuntu.com breezy-updates/restricted Packages
Hit http://es.archive.ubuntu.com breezy-updates/universe Packages
Hit http://es.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://es.archive.ubuntu.com breezy-updates/restricted Sources
Hit http://es.archive.ubuntu.com breezy-updates/universe Sources
Hit http://es.archive.ubuntu.com breezy-updates/multiverse Sources
Ign http://antesis.freecontrib.org breezy Release.gpg
Ign http://antesis.freecontrib.org breezy Release
Ign http://antesis.freecontrib.org breezy/free Packages
Ign http://antesis.freecontrib.org breezy/non-free Packages
Ign http://antesis.freecontrib.org breezy/free Sources
Ign http://antesis.freecontrib.org breezy/non-free Sources
Hit http://antesis.freecontrib.org breezy/free Packages
Hit http://antesis.freecontrib.org breezy/non-free Packages
Hit http://antesis.freecontrib.org breezy/free Sources
Hit http://antesis.freecontrib.org breezy/non-free Sources
Get:9 http://download.gna.org ./ Release.gpg [189B]
Hit http://download.gna.org ./ Release
Hit http://download.gna.org ./ Packages
Hit http://download.gna.org ./ Sources
Fetched 669kB in 19s (34.1kB/s)
Reading package lists... Done

```

Can someone give me a hand?

Regards.

---

### Post by joselin on 2006-01-21
I tried to apt-get update with an empty sources.list, and then restore my original file and apt-get update again, without success

---

### Post by fireonyx on 2006-01-21
It sounds like a problem with either your network card not installed correctly or maybe your network/firewall.  From the 2 machines that wont do apt-get, can you use the web as normal?  Have you tried to ping the servers listed as not being able to be reached?  Are those 2 computers behind a different firewall?

---

### Post by Kevbb on 2006-01-24
Hey Joselin..I had the same problem, and is now fixed. 
It was a mixture for me of the DNS servers being set up incorrectly (now set up as from isp, and not local network) and my firewall (Zonealarm) on my host pc being incorrectly setup...
I dont know if this helps, but I said I would let you know if I got mine resolved...
Cheers / Kevbb.

---

### Post by joselin on 2006-01-25
Hi all,

Before all thanks for your comments. Finally, i could solve it, the problem were the router. After restarting it, we could update the sources in all the computers. Seems that some ports were frozen, because i only restart it.

Thanks again.
Regards.

---

